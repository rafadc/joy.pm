+++
title = "A bit of machine learning with a Stratocaster"
date = "2023-05-25"
+++

I built [a tiny site to detect if in a given picture there is a photo of a stratocaster or a telecaster](https://resonant-puffpuff-92c2bd.netlify.app/).

Since we are in another AI surge I decided to write some pets in relation to machine learning. I was experimenting a bit with image categorization so I wrote one small web app. It is a super basic neural net to categorize if a photo contains either a Telecaster or a Stratocaster. Something that the world was not asking for but was really needed.

I built a small sloppy React UI on top of it. Do not be hard. It is my first React project.

![screenshot of the page](/posts/2023-05-25-a_bit_of_machine_learning/strato-or-tele.png)

Anyway the focus was on the machine learning side of things. Some learnings:

- Data cleaning is a PITA and takes a shitload of time. I spend a lot of time categorizing images. I tried to do a script to download a couple thousand from Duck duck go but at the end of the day I had to do a lot of validation manually.
- Iterating can get you to decent error rates. My first versions hace 30% error rate and I stopped at about 6 and taking into account that I am just a beginner probably this can be done far far better.
- Having a tough metric to fight like the error rate is super motivating. You run your training and evaluate your model against the testing set. It is super motivating to see how far you can go. It is far more rewarding than the green red cycle of TDD.

It was easier than what I expected though. I am super happy to see than in an afternoon I can hack something relatevely useful. Let's continue the journey!

Have fun!
