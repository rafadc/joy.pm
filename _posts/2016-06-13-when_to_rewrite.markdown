---
layout: post
title: "When to rewrite"
---

We all heard it. Probably some of us lived it. That beautiful moment when somebody asks: “why don’t we rewrite our full application?”

{% include image.html name="01.png" %}

## Things to consider before starting

I've always said that we humans have the beautiful power of learning from other people’s experiences so let me tell you mine:

- You will always lose features. Nobody knows completely what the application does up to the smallest detail. Nobody knows all the corner cases. Nobody remembers all the small decisions taking meanwhile wrig the application.
- A rewrite always takes longer than expected. Different orders of magnitude.
- Seriously. A rewrite will seem to be endless.
- A rewrite is a marathon, not a sprint. It’s chemotherapy, not some pills.
- The result may be better than what we had before in terms of speed, usability and maintainability. The problem is that the result may not be better and the customers may still prefer the old version.
- The sum of the cost may be smaller than the cost of evolving but you are not giving new value to the customers during the rewrite.
- If you improve the original application you are making the rewrite harder and maybe the rewrite becomes more expensive that adapting the old product. You are moving the target meanwhile you rewrite.
- If switching technologies you need all the team to be trained again. All of it. Not only coders.

## Why a big rewrite looks awesome?

- It puts a “fixed” date to the end of all your problems. It brings hope. Anyway careful about short (4–5 months) schedules. When you have a cancer you should not trust the shaman that says that it can be fixed imposing his hands.
- A rewrite has not to fight with hard truths because it is not in production by definition. You are making an imaginary product fight vs a real one.
- New and exciting technologies! Often the technical team is keen on the idea because it gives them the possibility of ditching the old system with all its defects and play with new toys.

## Things to NEVER do

- Switching technologies without taking the team into consideration. The team is going to maintain the product long-term wise. Make them part of it.
- Counter-strike rewrites: A terrorist comes, drops the bomb and then runs away. Maybe he hides and defends it for a while but he will finally gets the fuck out before everything blows up. Do NOT leave this to something whose future is not at stake in the rewrite. Do NOT make an external team alone to do the rewrite.
- Forget about the parts that brought us money of the old system since we are too focused on its defects.

## When you should make a rewrite
- When you are changing WHAT the application does. If the new app is remarkably different it is perfectly fine to rethink and rewrite. It may even be good idea freeing your hands from old restrictions.
- When you have some constraint that forces you to rewrite. For example, the programming language you are using will no longer be supported or works only in a weird kind of hardware that you will no longer have access to.
- You have reached the technology limit. You are Facebook, or Google or Google and Facebook together.
- When you are fully committed to it. You need to allocate a huge chunk of time just to do it. Be prepared to invest a ton of time and money on it.

## Bibliography ##

I leave this for the end because those are far better posts than mine:

- [Joel Spolsky on why you should never rewrite](http://www.joelonsoftware.com/articles/fog0000000069.html)
- [DHH on their success rewriting](https://signalvnoise.com/posts/3856-the-big-rewrite-revisited)
- [Dharmesh Shah on rewrites](http://onstartups.com/tabid/3339/bid/97052/How-To-Survive-a-Ground-Up-Rewrite-Without-Losing-Your-Sanity.aspx)
- [A chapter of the bike shed on rewrites](http://bikeshed.fm/58)
