+++
title = "org-edit-special and editing code in org mode"
date = "2017-02-25"
+++

One of the new funny things I found in emacs is org-edit-special.

I keep [my config files on GitHub](https://github.com/rafadc/emacs.d/blob/master/settings.org) in an org mode file.

Since I am in an org mode the snippets and indentation and all the stuff are from org mode major mode which is a pain in the ass. For that purpose: org-edit-special to the rescue!

<!--more-->

If we have an org mode file like the following:

{{< highlight elisp >}}
* Homebrew

I'll add homebrewe'd emacs packages to load path

#+BEGIN_SRC emacs-lisp
(let ((default-directory "/usr/local/share/emacs/site-lisp/"))
  (normal-top-level-add-subdirs-to-load-path))
#+END_SRC

{{< /highlight >}}

You can place the cursor inside the BEGIN-END block and press ```C-c '``` to invoke org-edit-special. Then you will open a new window where you can edit the code in the proper major mode with all your awesome customizations and snippets in place.

Happy coding!
