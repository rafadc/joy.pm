---
layout: post
title: "Compiling Emacs"
---

Let’s go bleeding edge!

{% include image.html name="01.png" %}

Just:

```
git clone git://git.savannah.gnu.org/emacs.git
./autogen.sh
./configure --with-ns
make bootstrap
make
make install
```

I’m compiling the OsX version. In linux probably you will not need the with-ns flag. After some minutes you own built Emacs.app will be in the nextstep folder. The last “make install” does not actually install anything but it just copies several things into the Emacs.app so it is ready to work. That step deceived me a lot because I lost some time trying to make the thing work due to me thing that would install something.

It will take a huge amount of time but that is life.

The last 25 version (at the moment of writing 24 is in homebrew) is blazingly fast so probably I will try to stick to this for some time.

There are some things that are a bit unintuitive. You can directly alias emacs and emacsclient commands. I had to create two shell scripts in my path like

```
#!/bin/sh
/Applications/Emacs.app/Contents/MacOS/Emacs “$@”
```

Now you can have at last a working emacsclient -nw.
Happy compiling!
