+++
title = "Software rots"
date = "2022-05-27"
+++

I had this discussion many times. Some people argument often that software are ones and zero and software doesn't rot because of that. If you don't change a software it doesn't change. It's only bits.

Ok. I'm fine with that. Maybe my problem is with the definition of what means for a software to rot. If I had to give a definition to what I mean for software to rot I'd say:

_The value a given piece of software provides changes over time. Almost always, this change is for its value to decrease._

That is what I mean with "software rots". There are many reasons for that. Let me elaborate a bit more.

## Software around you changes

Of course the most obvious case is that the software you have around changes. Let's imagine we are building a software that downloads all your Facebook posts into a single file. Maybe that is extremely valuable to you. If Facebook API changes your software provides no value until you adapt to that.

Ok, ok. Contrived example. I know your software does not connect to Facebook so you are immune to that. Aren't you?

For example in a previous job we used Redis. A lot. There was this funny little vulnerability. A Redis exploit that was discovered. Until we updated Redis our whole platform was vulnerable (in case somebody found a way to access it, but you can never say 100% you are secure). At that moment our software was less valuable for some hours. It is not a Redis issue. All the supply chain you are using to provide you service is a potential point of failure. Each day a failure is discovered you are vulnerable to an attack there and your value decreases. But wasn't that vulnerability there all the time? Yes it was. But the fact that now is public has decreased your value a lot.

Also, you may be hosted on a single cloud provider. You are reliying on them to provide your value.

## People change

There is this old notion of perceived value. Once your software is in production it starts losing the shiny brand new thing label slowly. The more time it passes users will start seeing its features as the new statu quo and it will feel less and less valuable to them.

Also, you are not the one writing software. There are more people providing brand new software that does something similar to what you software does. In a world with only one spreadsheet software this is extremely valuable but as time passes and when you have 50 different pieces of software doing that you need to do more things to provide the same value. It may be doing it faster, doing it cheaper or better but staying with the same 0's and 1's that never change will not make your software be equally valuable over time.

## Is this always so hard?

To be honest I think it sounds harder than it really is. It just means that we need to strive to improve, slowly but steadily. It is true that a piece of code will always be a piece of code but software is just a means to an end.

Also, not all software loses value at the same rate. I've seen services stay in production for years with no change at all. That is awesome. We should design products for that, but we are not always so lucky to hit the right spot.
