---
date: '2024-02-16'
draft: false
title: 'Anemic Models'
---

Disclaimer: This is an article on Object Oriented programming. I won't intentionally talk about other models like functional. I won't commit suicide today. Sorry XD

When doing Domain Driven Design we give a lot of importance to the modelling of the problem space we are working in. We should always do it in OOP but for some reason DDD has managed to strike a nerve we weren't able to hit before.

But let's start from the beginning. What is Object Oriented Programming?

![](/posts/2024-02-16-anemic-models/ooo.png)

In OOO we have objects that combine both data and behaviours. And they talk to each other in order to achieve a particular objective.

You can think that if you are using an object oriented programming language you are already doing object oriented programming style. It is not the case. There are a lot of situations that can cause not to be the case. Today I will focus on one of them.

Allow me to use Ruby as a driver for the discussion. I will try to keep it simple and understandable. I will make up also a "web framework" to put the focus in the topic at hand. Also I will be ignoring all dependency injection. I will maybe add a more complete example of pushing functionality to models in another post.

Imagine we are building a Book catalogue system. Somewhere in our system we have the following clases.

```ruby
class Book
  attr_accessor :name, :tags
end

class Tag
  attr_accessor :name
end
```

At some moment we are receiving a web request so we add a tag to a book. We can have something like this

```ruby
class TaggingController
  def add_tag(params)
    book = Book.find(params[:book_id])
    book.tags.append(Tag.new(name: params[:name]))
    BookRepository.save(book)
  end
end
```

Sometimes our objects stop being both data and state that talk to other objects and become just data structures. The importance is only in the things they contain.

We can take a bit of the behaviour and give it back to the objects for example in something like this:

```ruby
class Book
  attr_reader :name, :tags

  def apply(tag)
    self.tags.append!(tag)
  end
end

class Tag
  attr_reader :name
end

class TaggingController
  def add_tag(params)
    book = Book.find(params[:book_id])
    book.apply(Tag.new(name: params[:name]))
    BookRepository.save(book)
  end
end
```

This is a subtle change, I know. I am trying to do the most minimal example. But even if minimal we can see some interesting changes:

- We've put a name to the process of adding a tag to a book. We decided to call that "apply". Naming things is an important thing. This name should be decided alongside domain experts and become part of your ubiquitous language.
- We have changed from `attr_accessor` to `attr_reader`. We just constrained how a tag is applied to a book. The objects expose all that information.
- This is a bit contrived example since I want to keep is short but we can discuss if we want a tagging service that is the one that actually does that process. Normally I'd only have it if I consciously decide I want to have a [Transaction Script style](https://martinfowler.com/eaaCatalog/transactionScript.html)

If you compare the first objects to the second ones we can see that we are having more information about the domain model of the application too. They are not just bags of data. They are going from just data structures to objects.

It is not strange to see the first, more procedural, code style. We can start there as a mean to explore concepts and find good names for the domain model but eventually, if we want to follow an object oriented style we should move into the second direction.

Anyway, is this that bad?

Well, it is not like you are going to die in coding hell for this stuff but I find some advantages to the non-anemic model. It encodes more domain knowledge. Probably this is the most important thing for me. It forces you to put names to more activities in the domain so you can build an ubiquitous language for your context. That is often more valuable than any technical benefit. It is an opportunity lost in this context.

It is harder to model things this way, anyway. But that is not necessarily a bad thing.

Normally when we code in this style we end up either putting a lot of code in controllers or in [Transaction Scripts](https://martinfowler.com/eaaCatalog/transactionScript.html). While having code in controllers is clearly a bad practice having transaction scripts may not be that much bad as a crime. It is just that is somehow makes weird the choice of object oriented programming for the problem.

If you are going full object oriented, let's do it.

Happy hacking!

### Resources

- [Martin Fowler's bliki on Anemic Model](https://martinfowler.com/bliki/AnemicDomainModel.html)
- [Martin Fowler's bliki on Service Layer](https://martinfowler.com/eaaCatalog/serviceLayer.html)
- [Implementing Domain-Driven Design](https://bookwyrm.social/book/502855/s/implementing-domain-driven-design)

