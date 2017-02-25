+++
title = "Software rots"
draft = true
+++

I had this discussion many times. Some people argument often that software are ones and zero and software doesn't rot because of that. If you don't change a software it doesn't change. It's only bits.

Ok. I'm fine with that. Maybe my problem is with the definition of what means for a software to rot. If I have to formulate what I mean for software to rot I'd say:

_The value a given piece of software provides changes over time. Almost always, this change is for its value to decrease._

That is what I mean with "software rots". There are many reasons for that. Let me elaborate a bit more.

# Software around you changes

Of course the most obvious case is that the software you have around changes. Let's imagine we are building a software that downloads all your Facebook posts into a single file. Maybe that is extremely valuable to you. If Facebook API changes your software provides no value until you adapt to that.

Ok, ok. Contrived example. I know your software does not connect to Facebook so you are immune to that. Aren't you?

For example in Platform161 we use Redis. A lot. There was this funny little vulnerability. A Redis exploit that was discovered. Until we updated Redis our whole platform was vulnerable (in case somebody found a way to access it, but you can never say 100% you are secure). At that moment our software was less valuable for some hours. It is not a Redis issue. All the supply chain you are using to provide you service is a potential point of failure. Each day a failure is discovered you are vulnerable to an attack there and your value decreases. But wasn't that vulnerability there all the time? Yes it was. But the fact that now is public has decreased your value a lot.

# People change

There is this old notion of perceived value. Once your software is in production

# World around you changes

All you integrations can fail. APIs get deprecated and services disappear.
