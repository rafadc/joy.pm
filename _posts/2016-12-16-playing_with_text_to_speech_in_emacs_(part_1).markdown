---
layout: post
title: "Playing with text to speech in emacs (part 1)"
crosspost_to_medium: true
---
Amazon has just announced Polly and I wanted to give it a try. Of course the first thing that came to my mind was: [elfeed](https://github.com/skeeto/elfeed)! Polly is not free but 4$ per 24 hours seems reasonable in order to read a post from time to time. Anyway let's start there, get the ball rolling, and if it works well maybe we can think in adding more backends.

So, let's go to work!

I was trying the command line and it looked good enough for me. If you have aws-cli tools installed it is enough a mere:

{% highlight bash %}
aws polly synthesize-speech \
    --output-format mp3 \
    --voice-id Joanna \
    --region eu-west-1
    --text "We are about to have a lot of fun!" \
    hello.mp3
{% endhighlight %}

to get an mp3 downloaded into your machine. With that, probably we can have just enough.

Let's go to emacs. I just added to my config the following function:

{% highlight elisp %}
(defun my/elfeed-send-to-tts ()
  "Send current article to a text to speech system"
  (interactive)
  (let*
    ((html-to-read (elfeed-deref (elfeed-entry-content elfeed-show-entry)))
     (text-to-read (replace-regexp-in-string "<.*?>" "" html-to-read))
     (temp-input-file (make-temp-file "elfeed-input-tts"))
     (temp-output-file (make-temp-file "elfeed-output-tts" nil ".mp3"))
     (polly-command (concat "aws polly synthesize-speech --region eu-west-1 --output-format mp3 --voice-id Joanna --text \"$(< " temp-input-file ")\" " temp-output-file )))
    (progn
      (write-region text-to-read nil temp-input-file)
      (shell-command polly-command)
      (shell-command (concat "open -g " temp-output-file)))))
{% endhighlight %}

Elfeed retrieves the content in HTML so the first thing I have to do is get the raw text

{% highlight elisp %}
((html-to-read (elfeed-deref (elfeed-entry-content elfeed-show-entry)))
 (text-to-read (replace-regexp-in-string "<.*?>" "" html-to-read))
{% endhighlight %}

Then, in order to be easier to me to work with the command line I just created a temporary file to store the text and a temporary file that will hold the mp3 of the text

{% highlight elisp  %}
(temp-input-file (make-temp-file "elfeed-input-tts"))
(temp-output-file (make-temp-file "elfeed-output-tts" nil ".mp3"))
{% endhighlight %}

I still need to investigate if the output file is correctly disposed since I will be overwriting it with the shell.

The rest is pretty obvious. We just prepare the command:

{% highlight elisp %}
(polly-command (concat "aws polly synthesize-speech --region eu-west-1 --output-format mp3 --voice-id Joanna --text \"$(< " temp-input-file ")\" " temp-output-file )))
{% endhighlight %}

then prepare the input and fire the command

{% highlight elisp %}
(write-region text-to-read nil temp-input-file)
(shell-command polly-command)
{% endhighlight %}

I'm using a little bash trick

{% highlight bash %}
$(< input_file)
{% endhighlight %}

That will put the file contents in the command. Probably I will have to escape the output somehow but this is my first approach. Let's add this to the TODO list and continue.

Finally to play it I will use another dirty trick. This will only work in macOS at the moment.

{% highlight elisp %}
(shell-command (concat "open -g " temp-output-file))
{% endhighlight %}

This will open the default mp3 player in the background and read the text.

With this we have:

<iframe width="560" height="315" src="https://www.youtube.com/embed/Tvjc9eVG1uo" frameborder="0" allowfullscreen></iframe>

So at least we have something working. We have still some problems with escaping the input text. Also I found that the command line has a limitation of 1000 characters. We will deal with this problems in further posts.
