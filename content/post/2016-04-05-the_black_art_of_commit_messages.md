+++
date = "2016-04-05"
title = "The black art of commit messages"
+++
Good commit messages are the unicorn of the person maintaining legacy code. I will try to review some commit messages I’ve found over the years with its pros and cons.

I’ll break this into two categories: solving bugs and adding features.

<!--more-->

## Solving bug commit messages

The brief

```
Fixing code
```

**Pros**: At least it is not destroying code
**Cons**: What the hell is happening there? I can commit anything under that excuse

More specific brief

```
Fixing bug
```

**Pros**: At least it is not introducing bug.
**Cons**: What the hell is happening there?

```
Making it work again
```

**Pros**: It is working… again
**Cons**: Why wasn’t it working before?

```
Fix bug in module X
```

**Pros**: Module X has one less bug
**Cons**: At least I have a bit more context. Too bad I could deduct that information from the diff.

```
Fix #23344
```

**Pros**: I have a ton more context of the reason behind the error. Unfortunately I don’t have it immediately. If I use a modern issue tracking system I can navigate to a discussion regarding this bug from my browser or editor.
**Cons**: I have to go to my issue tracking system

```
Fix #23344 Removing n+1 problem
```

The problem was that these lines were causing a nasty n+1 problem because we have a lot of entries in our “users” table.

**Pros**: I immediately have all the context of why the change was made and what the guy that had written this piece of code thought he was doing.
**Cons**: A bit verbose sometimes

## Adding feature commit messages

```
test / testing / just testing
```

**Pros**: The code is probably tested
**Cons**: Everything else

```
Renaming method
```

**Pros**: Probably the new name is better
**Cons**: I saw it in the diff already. Why it is a better name?

```
Refactor
```

**Pros**: No behaviour was changed.
**Cons**: Just kidding. Please, tell me why you needed to refactor this.

```
Applying observer pattern
```

**Pros**: You know at least one design pattern.
**Cons**: Why is that a good idea in that scenario?

```
Added new stories notification

This feature was requested in #112233

We are adding two new methods in the API so we can integrate in the future easier in our mobile app. These methods are now used in the frontend only.
```

**Pros**: A lot.
**Cons**: Verbose

## Putting it all together

When I look into a commit message, often, I am desperately looking for the reason why the change was made. I don’t want to know what changed. There is a diffing tool for that. It does not hurt if it is briefly describe what is done in the commit message but the most important part is why the change was made. When I read a commit message it often means that I am investigating a problem in the code so I need to know your assumptions to see if you were wrong or the assumption is now not valid.

Have some empathy with a person investigating something wrong with your work, most probably, your future self.

{{< figure src="/posts/2016-04-05-the-black-art-of-commit-messages/01.png" >}}

With the diff I can already see what changes were made. The text just explains what the hell I was trying to do and more importantly why. This gives the investigator a great deal of information to know if I was wrong in case something needs to be fixed.

This is one of the reasons I am starting to avoid using the -m switch of git commit

```
git commit -m “I did something with the code”
```

If we commit like that we are encouraging small commit messages and it becomes too tempting not to explain a little bit to the next programmer.

That is, also, why these days I’m embracing the idea of interactive rebasing my branches before merging to the main branch. This gives me some introspection time to organize the commits appropriately and reword some commit messages to make the lives of future readers better.

Now probably a ton of people will come with better ideas than this for commit messages. New ideas are welcome.
