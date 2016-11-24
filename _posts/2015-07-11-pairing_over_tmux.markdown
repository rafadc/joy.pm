---
layout: post
title: "Pairing over Tmux"
---
Tmux is an awesome tool. One of its greatest uses is that is allows us to pair if you share the session. Anyway the setup is always a little bit complicated if you want to do it really right. Let’s see what we can do.

# The simplest scenario

Let’s start in our computer all alone. Tmux sessions are run by a daemon the same way as screen does.

Let’s create a new session where we will pair

```
tmux new-session -s pair_programming
Now if you open a new terminal window you can attach your console to the same session.
tmux attach-session -t pair_programming
```

Then you are sharing the session in the same computer. Easy, isn't it?

![Both terminal sharing a common tmux session](/assets/2015-07-11-pairing_over_tmux/01.gif)

Even this may be impressive it’s not very useful.

# In the same network

Now let’s try something a bit better.

We just saw that we can share a tmux session between two terminal sessions. Then we have a simple way of sharing the session over the network. We can simply make other user to ssh into your computer and run tmux from there.

Wait… Am I saying that it is a good idea to share your account with your pair? No, don’t get me wrong. We can do a couple of things to prevent this:

First, it is a good idea to create a local account only for your pairs. For example i've created an account called pair in my computer. Also it is a good idea to create a tmux group as we will see later. Add both your user and pair user to that group.

Also instead of sharing the password for that account I’m using certificates to handle who has access. That way it is super easy to revoke the access once it is no longer necessary. There is one awesome gem called github-auth that simplifies a lot the process. I can make something like

```
sudo su - pair
gh-auth add --users=<my pair’s Github user>
```

And it will allow my pair to connect to my laptop without having to deal with passwords or stuff like that. Also the pair user has access to tmux so he can connect to my session and finally he can’t access to anything else in my computer.

Also I can revoke access as simply as doing

```
sudo su — pair
gh-auth remove --users=<my pair’s Github user>
```

How does this work? Well, this works because all our Github public keys are public. You can access yours through a url like:

```
https://github.com/<your username>.keys
```

Then this is using ssh’s authorized keys to allow a user to login as pair user without having to type his password.

Let’s test this. I’m login with pair user and let’s see if I can connect to one of my tmux sessions:

```
tmux ls
failed to connect to server: No such file or directory
```

What? Isn't this enough? Well… no. Unfortunately we need to add an extra small step. When we start a tmux session we need to provide a socket so it is shared between different users. Let’s start our pairing session with that new parameter:

```
tmux -S /tmp/tmux_pair_socket new-session -s pair_session
```

And we have created a new session and also exposing a socket so the other user can connect. The bad thing with this approach is that the socket will have wrong permissions for sure. That’s when the tmux group comes handy. I’ve created a /var/tmux/ folder and gave it 770 permission and changed the group to tmux. This way we can hold the socket there and change the property of the socket to tmux group.

```
mkdir /var/tmux
sudo chmod 770 /var/tmux
sudo chgrp tmux /var/tmux
```

Then let’s create the socket there.

```
tmux -S /var/tmux/pair_socket new-session -s pair_session
```

And we will be able to see it from pair user.

```
$ tmux -S /var/tmux/pair_socket ls
pair_session: 1 windows (created Sat Jul 11 11:40:08 2015) [78x30] (attached)
```

And attach to it with

```
tmux -S /var/tmux/pair_socket attach -t pair_session
```

So. After all this config I only need to ask my partner to do:

```
ssh pair@<my IP>
tmux -S /var/tmux/pair_socket attach -t pair_session
```

And we will be sharing the terminal session with a super fast latency.

# Easing things a little bit

Anyway still the user I’m pairing with needs to know the location of the socket. Let’s make the things a little bit easy for him.

We will make a small addition to /etc/sshd_config file so the pair does not need to remember anything.

```
Match User pair
  ForceCommand /usr/local/bin/tmux -S /var/tmux/pair_socket attach -t pair_session
```

Then if some pair tries to login into my computer and there is no pairing session prepared it will only output an error and if there is it will directly connect to it. Piece of cake!

Also to start a new pairing session I’ve added an alias to my .zshrc

```
alias pair_tmux=’tmux -S /var/tmux/pair_socket new-session -s pair_session’
With all this I only have to type in a terminal:
pair_tmux
```

and my pair just has to

```
ssh pair@<my ip>
```

And if the credentials are correct we just need to start coding!

Also I have the following alias to add permissions

```
alias pair_adduser='sudo -u pair -i gh-auth add — users '
alias pair_removeuser='sudo -u pair -i gh-auth remove — users '
```

This way I don’t need to switch user to give permission to somebody to the pairing environment.

# Firewalls

Let’s say that you want to host a session and you are behind a firewall. If you don't want to change your firewall rules and you have a public host you can as a last resort try to do a reverse tunnel.

If you don’t have your own host you can try using ngrok. It creates a reverse tunnel for you so your pair can connect to it. We can just do

```
ngrok tcp 22
```

And we will have a tunnel open that will be available to your pair through the URL that appears in the screen. For example in the following scenario

![ngrok details](/assets/2015-07-11-pairing_over_tmux/02.png)

Our pair will have to connect using the following command

```
ssh pair@0.tcp.ngrok.io -p 54147
```

And that is it!

Just as a piece of advice avoid the homebrew version and download from their website. Ngrok client is no longer open sourced and homebrew will not be up to date.

Ngrok will also be free as long as only one client connects to your TCP socket. If you need more that one person their pricing is really reasonable.

# Conclusion
It takes a little bit of work to set up a nice setup to pair using tmux but it is worth the effort. In the works case scenario I only need to

```
pair_tmux
ngrok tcp 22
```

And share a URL for may pair to connect. Piece of cake.
With this and a hangout I can pair with only a tiny little bit of lag and both users have control of the editor.
