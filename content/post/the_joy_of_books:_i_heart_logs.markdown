+++
title = "The joy of books: I heart logs"
draft = true
+++

The latest addition to my library is [I heart logs](http://amzn.to/2juQhQk)

![Cover](http://akamaicovers.oreilly.com/images/0636920034339/cat.gif)

I started reading it because we are starting to struggle to manage the logs on our application and this is indeed a book that makes you think.

I've always considered logs as tiny pieces of text stored for diagnosing problems but the book soon changes your view defining them as a list of events of what happened in the system. While we are working with a small application those small unformatted pieces of text are enough for us and maybe that is why we never move away from that definition. But one we scale a multi-machine deployments the problem of aggregating all the things that happened throughout the system in a given moment in time is trickier.


Meanwhile I was reading this I recalled an interview with Kent Beck in Java magazine (I cannot provide link since they onl provide PDF) where he speaks about the important of reversibility in some situations more than careful testing. I am starting to explore that mindset lately and it is sharing the spirit in this book. Logs are key if you want to know what happened. You can never log enough because you never know where your failures are going to happen.

The logs are really a database of events that happened in your system. Once you start thinking that way you start to get afar from that small idea of text chunks in a file. Once things start to get bigger you need to structure your logs and use things like JSON logs. You need to process them programmatically for example with an ETL tool like Logstash. You need to process them and prepare a visualization over them.

But we can go further. The book points out this: "Take all of the organization’s data and put it into a central log for real-time subscription." Which is an extremely interesting sentence with huge implications. You have a huge event store in your logs. It is fun that we use them only to read through them.

As I advance through the book I lose the concept of logs as lined of text in a file but another data structure of our application that may be stored in a file or replicated across multiple places.

The case for logs as the real data for example in rtb systems.  The book takes the example of LinkedIn which is very similar
