+++
title = "Predictability, estimations, nobel prizes and powerful people"
date = "2021-03-16"
+++

I've had this conversation so many times I have to turn this into a blog post.

This is a controversial topic. I understand that some people need estimations and I may not be an authority to rant about this but... this is my personal space :-).

A lot of times when dealing with software projects we say we are optimizing for predictability. We want to build projects in such a way that we know beforehand how much it is going to cost. That may be a noble outcome but I think optimizing for that is a rabbit hole that can lead us to many problems that we didn't consider in the beginning.

We are trying to fundamentally go to a model where teams are predictable and we are doing so by providing teams with the adequate processes and tools so they can estimate and do their jobs better. This sounds reasonable. In my humble experience, it is not. Not only unreasonable, it is toxic.

There is more than one fundamental problem here.

## Turning estimations into commitments or even deadlines

When you want to be predictable you are aiming to be able to say "hey, this will be finished by this date".  Often, we do this by asking the team when they think they will have something finished and immediately assign that a certain degree of truth. No matter how hard we try science goes against us. This is not a problem that only software development teams have.

In 2002 [Daniel Kahneman](https://en.wikipedia.org/wiki/Daniel_Kahneman) won a Nobel prize for "his groundbreaking work in applying psychological insights to economic theory, particularly in the areas of judgment and decision-making under uncertainty.". This sounds a lot like estimations to me. And his findings are totally against what we are doing in software developmentworld. You can see an example in [[1](#cit1)]. Estimations should be more "outside in" driven by comparisons and previous art than "inside out" by having engineers being in a negotiation to get the smallest possible date.

I don't know when we turned this Agile trend into having a team of engineers agreeing on having this done by a date but we did. The more software teams I talk about estimations the more I see business using them as if they were kind of an informed guess instead of just a random number.

Kahneman found something really groundbreaking. Often, the more we know about a given task the more biased we are to underestimate it. Indeed, most of the times people that estimate tasks by comparing to other similar things without knowing the details get better estimations than the experts in doing that task. Kanheman has a Nobel prize. We don't. Kahneman 1 - Software Engineers 0. Probably we should read less Uncle Bob and more behavioral economics but that is the topic for another blog post.

## Then, are estimations worthless? Hell, no!

We should estimate. We have clear the concept that estimations should be made. But I disagree in two important parts. Who should estimate and what is the reason for estimating.

If you managed to read all this until now and you have learn a bit from Kahneman's story, having an outside view is not only important but paramount in guessing when things will be finished. In my experience, in most of the companies I've seen only developers take part of it and the rest of the people in the room (if there is any) taking the "you are the experts" kind of attitude.

Why do we estimate then? We want to know when a project will be delivered. But if you agree on the Nobel-prize-evidence-based premise (wink, wink) why are we just onboarding engineers on it? Indeed they are the worst people to do it if you believe in the premise before. Why are our estimation process based on letting the devs guess instead of doing other practices?

What is worse. What do we do when things go south? You can change three things: scope, date or resources. None of those can be changed by the people you are making responsible of the dates.

Again let me use another fallacy of appealing to authority and cite Ron Jeffries [[2](#cit2)] "Management has the responsibility to set the overall goals, the resources, and the date. The Product Owner, or the Customer, has the responsibility for giving us the best combination of features so that we meet as many of the goals as possible by the date. Development has the responsibility to deliver a smooth sequence of fully integrated software versions, at least monthly, containing an always-growing collection of running, tested features, as specified by the Customer and by Management.".

Let me repeat. If someone is guilty of not making deadlines that is management because reaching dates is his job. I don't know when they lost it.

It is always fun to try to explain your job to your grandmother when you are a software developer but, ideally, the purpose of your job should be simple and the goal of software developers should be "deliver the best software you can". That's it. They shouldn't juggle on "should I add a one month buffer here so my job is safe?". The management layer's goal is "deliver on date" and take actions on the items we mentioned before if it looks like we are not reaching the date. We have agile coaches that are supposed to help the team to introspect so they don't forget being a bit better each day. When did we change this?

## Toxic implications in being predictable

We all want to keep our jobs. No one wants to look bad in public. If we are forcing people into being better at estimating and praising people when they get it right a lot of teams will start being predictable. Probably not because people do this intentionally but we will create a Darwinian process where people doing the wrong thing will be empowered and said they are doing the right thing. And that is terribly bad.

- Everyone will be adverse to risk so they will pursue worse outcomes in lieu of being more predictable.
- No one will automate. Why should we? If you do the same task over and over again you are able to estimate better how long it will take. You are able to create cookie cutter sized jobs instead of creating a cookie cutter machine so that task is no longer a problem. Indeed, being able to estimate reliably is often a sign of lack of innovation.
- Underestimating is punished, overestimating is totally fine. This forces everyone into leaning towards underestimating which creates the weird situation where we say that we can have something done by a given date we both lie conscious and unconsciously at the same time.

And sometimes we ask ourselves: Why building software in some enterprises is so hard? Mostly because they asked for it.

## What is the model I am advocating for here?

Let's be constructive and propose alternatives.

Think of teams as a black box. We need to ensure they are doing the best they can, whatever that is. We should be on top of them so they deliver "their best job ever". Quote: "A business leader's job is to create great teams that do amazing work on time. That's it. That's the job of management." [[3](#cit3)] The management layer over the teams should be on top of the team (not only the individuals but the team) and use all the tools at his disposal to train them to perform the best they can. The team should forget about dates and do their best. The management should juggle with dates, scope and resources to reach deadlines.

The people management layer needs metrics and tools to help the team find areas where to improve. Velocities, estimations, KPIs and such things are tools the manager has at his disposal so everyone can decide what to experiment on and check the metrics again to validate if those experiments are worthy or not.

I can only see two reasons for a team to do estimations. First, to serve as a way of discussing what needs to be done and align what the end goal is in the heads of people and second so the team can calculate velocity. If you do the first one you don't even need to annotate the results and if you do the second one turning things into a date should be enough to detect you are doing it for the wrong reason :D.

## A team should be closer to a sports team in the sense of pursuing improvement

A team should be closer to a soccer team than to a family [[3](#cit3)]. We should be creating teams pursuing excellence instead of pursuing just getting the estimated date right. Estimations and in particular velocity calculations is just one of many indicators a team may have to self assess better.

If teams innovate and try to constantly improve they may have a panel of metrics and indicators on themselves same as we have Grafana dashboards for our software. It is fine if the team decides that velocity is one of the metrics they want to have. And to calculate that you need estimations.

So yes, sometimes we should estimate and it needs to make sense to track those estimations but what is important is the continuous improvement and not the dates we get from there.

# {#cit1}

[1] Kahneman excerpt from thinking fast and slow: [https://www.mckinsey.com/business-functions/strategy-and-corporate-finance/our-insights/daniel-kahneman-beware-the-inside-view#](https://www.mckinsey.com/business-functions/strategy-and-corporate-finance/our-insights/daniel-kahneman-beware-the-inside-view#)

# {#cit2}

[2] Ron Jeffries. The nature of software development [https://ronjeffries.com/xprog/articles/jatmakingthedate/](https://ronjeffries.com/xprog/articles/jatmakingthedate/)

# {#cit3}

[3] Patty McCord. Powerful: Building a Culture of Freedom and Responsibility

Have fun!!
