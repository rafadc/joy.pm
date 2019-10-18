+++
title = "Dry monads"
draft = true
+++

These days I've been using more throughly the [dry-rb gems](https://dry-rb.org/) so I wanted to spend a little bit of time preparing some code and writing a bit about them.

I will start with one of the ones that have shocked me the most, [dry-monads](https://dry-rb.org/gems/dry-monads/1.0/). It surprised me because it explains extremely well what is one of the concepts that has been more difficult to grasp for me: the monads.

You can always [search stack overflow](https://stackoverflow.com/questions/3870088/a-monad-is-just-a-monoid-in-the-category-of-endofunctors-whats-the-problem) but sometimes I find easier to just start with the code and then run into a vague idea of what I am working for.

So let's start our journey with the amazing Tom Stuart with his beautifully simple explanation:

[![Refactoring with monads](http://img.youtube.com/vi/J1jYlPtkrqQ/0.jpg)](http://www.youtube.com/watch?v=J1jYlPtkrqQ "Refactoring with Monads")

So let's try to explain the monads that dry-monads offer to see if we can build a more sustainable ground.

Let's base our code in the following scenario

```ruby
require 'dry-monads'

Author = Struct.new(:name)
Blog = Struct.new(:posts)
Post = Struct.new(:text, :author, :comments)
Comment = Struct.new(:text, :author)
```

So we have blogs that have posts that have comments. Let's create a bit of seed data.

``` ruby
rafa = Author.new('rafa')
john_doe = Author.new('john doe')

joy_of_programming = Blog.new('The Joy of Programming')

dry_monads = Post.new('Dry monads is cool', rafa, [])
dry_monads.comments << Comment.new('Hey, cool stuff', john_doe)
dry_monads.comments << Comment.new('Thanks mate!', rafa)

```


## Maybe

Let's start with the one whose concept is probably the easier to understand. Maybe's purpose is to access a value in a chain when we have nils in the chain where we are accessing it.

Null values [are the billion dollar mistake](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/) and we can live without them. The Maybe monad offers a beautiful interface for us to deal with values that may or may not be there.

With our seeds
