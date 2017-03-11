---
layout: post
title: "Clean Code — My Methods and Reasons on Writing Clear and Concise Code"
categories:
  - Code
tags:
  - Code
---

Writing clean, concise and maintainable code can be a tricky matter if it’s your first time thinking about it. Because if it’s your first time, this can mean many things to you, but that thought it’s self is a good first step. Clean code, is to understand that the code you are writing is no longer for yourself. The code you now write, is for someone else to read. That someone else can even mean your future self two days from today.

Writing code for others, means you can’t have a coding style simply because you like writing code that way. You have to find out what the convention for that language is and start writing along those conventions. If Ruby’s variable naming convention is underscore instead of camel case like JavaScript. Then you write underscores instead of camel case for other Ruby developers to be able to read. Still before we get to unique conventions there are still very universal conventions.

## The Weight of Bad Code

Writing bad code can be a big weight on your project. Imagine writing bad code where you can still understand it. Then you start to add more code onto it and it becomes increasingly complex. Then you don’t touch the code for a couple of days until one day you decide that you’d love to add a feature onto it. Until you realize you’re now stuck with the gruesome task of trying to re-understand everything that’s going on with it. Now imagine once you figure it all out, you tweak a piece of the code and it breaks in three different places and you don’t understand the path the code is taking to tackle the bug. Your productivity is basically non-existent. This makes code

## Naming Variables

So lets start with some basic, mostly universal clean code which I’ve written in Ruby, but they can be used for any language in general.
Lets start with name variables, if you’re naming variables, then name them exactly what they are. If you’re talking about a car, name your variable car. Don’t take shortcuts, because a shortcut ‘c’ now means car, but a shortcut ‘c’ might mean cat in the future.

Bad :
```ruby
n = "Bob"
c = "Mustang"
```

Good :
```ruby
name = "Bob"
car = "Mustang"
```

## A Set Should Become A Classes

Clean code on classes can be an entire blog on its own, but to begin with you must know when to use a class instead of variables. This happens whenever you notice a pattern or repeated keyword for a set of variables.

Bad :
```ruby
personName = "Steve"
personAddress = "456 street state 98456"
personEmail = "email@mail.com"
```

Good :

```ruby
class Person
    def initialize(name, address, email)
        @name = name
        @address = address
        @email = email
    end
end
```

## How To Name Methods

Methods take an action and should name it the action it’s taking. This way if you have a method that’s counting the number of people on a line, it reads “Count line” like a human sentence.

```ruby
line = ["Steve", "John", "Rob"]

# method call
def count(line)
```

Your methods also have to be predictable. As programmers you’re use to methods having a way of being predictable the same way you expect a game controller to have somewhat of a very similar layout regardless of console. Methods have to be the same way .

## Pure Methods

Methods should almost always have a non-destructive method before a destructive version of that same method. What I mean is that if you have an array that concatenates the word ‘meow’ to the passed string argument, it should not alter the passed variable. Pay attention to the difference in console outputs.

Bad :
```ruby
sentence = "The cat goes"
meow_sentence = concatMeow(sentence)

puts(sentence)       # "The cat goes meow"
puts(meow_sentence)  # "The cat goes meow"
```

Good :
```ruby
sentence = "The cat goes"
meow_sentence = concatMeow(sentence)

puts(sentence)      # "The cat goes"
puts(meow_sentence) # "The cat goes meow"
```

## Single Responsibility Rule

The single responsibility rule is to make sure a method does one job and only one job. The reason because you may want one functionality and not the other. For example lets say you had a function that takes a name, then later you want to just display the first name on their profile page instead of the full name.

```ruby
def main()
    name = get_full_name()

    puts(name)
end
```

Single
```ruby
def main()
    first_name = get_first_name()
    last_name = get_last_name()

    puts("#{first_name} #{last_name}")
end
```

## Should I Comment my Code?

This is a big debate amongst programmers, I’m sure it’ll even cause some to say my entire blog is invalid because of this, but to be straight to the point, people should be able to read your code without comments. Because comments arise another problem along with maintaining your code. Maintaining your comments.

The problem with comments, is that comments don’t have errors thrown if they’re the wrong comment for the wrong piece of code. If my function counts the number of items in an array and I comment saying that my function displays the thriller video, then on runtime it will not throw an error. You can now imagine if you comment your code well, but someone else decides to rearrange the code without any regards to the comments.

What you write :
```ruby
# Name of Person
n = "Steve"

# Prints someone's name
def display(n)
    puts(n)
end
```

Someone else who doesn’t care about your comments, makes some edits. Changes your variable into a list of names and changes your function to returning the count of names:

```ruby
# Name of Person
n = ["Steve", "Fido", "Roman"]

# Prints someone's name
def count(n)
    return n.length
end
```

What you should practice :
```ruby
name = "Steve"

def display(name)
    puts(name)
end
```
