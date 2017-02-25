+++
date = "2016-12-18"
title = "Taking notes and coding"
+++

I am not such a big fan of paper. I don't know. Maybe it is just me but I found it extremely inconvenient for taking notes on how code should work. It is too far away for my development environment. They are difficult to share, specially in a remote environment, easy to lose and difficult to transform. Also on paper everything looks easy and good ;)

<!--more-->

I have used several alternatives for different situations:

## Writing pseudocodish code

I've seen a lot of people writing notes like:

{% highlight pseudocode %}
Get all the customers
Find the oldest group
Send a complicated email to them
Find the youngest ones
Send a twitter message
{% endhighlight %}

IMHO taking that as notes is absurd. How does that differ from throwing out a method that reads

{% highlight ruby %}
oldest_customers = Customers.oldest
send_complicated_email oldest_customers
youngest_customers = Customers.youngest
send_twitter_message youngest_customers
{% endhighlight %}

Use the code as your notes. You are forcing yourself to make yourself clear there. Then you just need to fill the gaps.

If you want to TDD you can then start with the tests that will prove if that code you are trying to write makes sense or not.

## Using a personal_notes.org file

In my emacs I bound F7 to a personal_notes.org file in the root of the git repo I'm currently in. That way I can quickly jump to a sketchbook where I can plate bits of text that I want to keep for whatever reason.

## Using artist mode

If for some reason I need to draw some quick figures I can use artist mode. It is not extremely elaborated but it makes the trick a lot of times.

You can find an example of what I am talking about in [this screencast](http://cinsk.github.io//emacs/emacs-artist.html).

## Using org-capture

[Org capture](http://orgmode.org/manual/Capture.html) makes extremely easy to set reminders of things you need to do in the future. With a key binding I can save a small text regarding what I need to do plus a link to the location where I saw the problem.

I keep different files for different purposes. One for features that would be awesome to add, other for the code that should be refactored, other for topics to raise in the retro and some smaller ones for ongoing projects.

This allows me to just concentrate in the task at hand and leave the rest for a better moment.

## Just not writing it down

Ok, you can do this on paper but this is a friendly reminder that you don't always need to write down everything. Just let some things go. Storing all your ideas may be too much. Keeping track of notes has a cost too that needs to be leveraged.
