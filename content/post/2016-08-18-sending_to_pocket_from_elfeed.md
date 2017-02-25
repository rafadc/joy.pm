+++
date = "2016-08-18"
title = "Sending to pocket from elfeed"
+++

I often use elfeed to go quickly through my RSS subscriptions. There are some of them that I want to take more time to read.

<!--more-->

{{< figure src="/posts/2016-08-18-sending-to-pocket-from-elfeed/01.png" >}}

Yes, it is mostly text but it is super useful.

I send the entries that I need more time to read to pocket. I do that because I can use pocket client in my mobile phone or in the desktop or wherever the hell I am. I can also use any spare moment in the bus or the airplane even without internet access.

Elfeed by default has nothing like a pocket integration but as you’ll probably know emacs lisp is always here to help.

One of the less known pocket features is the possibility to send links via email. We will make good use of it. Remember that you need to send the email from the same email address you have in pocket.

{{< figure src="/posts/2016-08-18-sending-to-pocket-from-elfeed/02.png" >}}

In order to send emails I am using Msmtp. My configuration for gmail is something like:

```
account default
host smtp.gmail.com
port 587
protocol smtp
auth on
from my.email@gmail.com
user my.email@gmail.com
password application.password
tls on
tls_nocertcheck
```

Remember to create an application password for this. Never use your main password ;)

Msmtp is a beautiful tool to send email. You can send an email from the command line just with:

```
echo "Hey!!!!" | msmtp recipient@mail.com
```

That said let’s create the binding in elfeed config. If we check the source for elfeed show we can see that we can retrieve the URL of the current entry with:

{{< highlight elisp >}}
(elfeed-entry-link elfeed-show-entry)
{{< /highlight >}}

Piece of cake. Let’s then let’s define an interactive function to send the email:

{{< highlight elisp >}}
(defun elfeed-send-to-pocket ()
  "Send current article to pocket"
  (interactive)
  (let
    ((url (elfeed-entry-link elfeed-show-entry)))
    (shell-command (concat  "echo '\\n\\n" url "' | msmtp add@getpocket.com"))
    (message "Saved to pocket!")))
{{< /highlight >}}

I always add the final message to remember what is happening and avoid having an impossible to understand message like “Shell command successful” in the editor.

Now in my use-package for elfeed I only need to add the following in the config section

{{< highlight elisp >}}
:config
  (bind-keys :map elfeed-show-mode-map
                  ("x" . elfeed-send-to-pocket))
{{< /highlight >}}

This way when in an article I can just press x and the article will be saved to pocket.

Happy emacsing!
