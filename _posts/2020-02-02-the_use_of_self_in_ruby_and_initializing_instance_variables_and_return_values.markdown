---
layout: post
title:      "The use of Self in Ruby & Initializing instance variables  & Return Values"
date:       2020-02-02 20:12:30 +0000
permalink:  the_use_of_self_in_ruby_and_initializing_instance_variables_and_return_values
---


Before I started this blog, I thought that self was mostly used for the Classes and Modules.  I knew there were instance methods that self represented but I didn’t think it was that often.  Let’s start at the beginning though….

**What is Self?**
Self in Ruby gives you access to the current Object.  The method that’s using Self in the top of the method name, like this is, calling it on a Class.  So Self is the Dog.   
```
class Dog
      def.self bark
puts “Woof!”
      end
  Dog.bark
End

```


**To Explain:**

A method call in Ruby is the sending of a message to a receiver, which is an Object in Ruby.  It means that every piece of code you write "belongs" to some object.  
So, if your new to coding, start asking yourself “What Object each method belongs to?”  “Is it the Class that owns it?”  Or is Self an instance variable? An instance of the method its being used in.

Self is a set apart variable in Ruby that points to the object that "owns" the currently executing code.
This seems straight forward until you try to separate self Class methods from the times self is used as an instance variable. 
 Ruby uses self everywhere so its good to get used to telling yourself when it’s an instance of the method or the Class method itself?
Ruby also lets you show the difference in Class variables by using one or two @ signs like this:
```
@name         is instance variables
@@name     is Class variables


```


**Initializing Instances:**
 
You can initialize an instance like this, we’re creating an instance of a childs gifts.
Here were using setter and getter methods to initialize gifts.
```
class Child
  def initialize(gifts)
    @gifts = gifts
  end
 
  def gifts=(gifts)
    @gifts = gifts
  end
 
  def gifts
    @gifts
  end
end
```

**And now we can call new ones like this:**
```
aubrey = Child.new #=> #<Child:64564575635657>
aubrey.gifts #=> nil
aubrey.gifts = “Dancing”
aubrey = "Dancing"
clover = Child.new("Art") (This is creating a new instance of Child and setting her name as the new variable.  She is an instance of a Child)
 
clover.gifts #=> "Art”

```
**Or, **
**We can use an initialize method, like this:**
```
class Child
     attr_accessor  :gifts

  def initialize(gifts)
    @gifts = gifts
  end
 end
```
**Now, we can call a new instance like this:**


```
aubrey = Child.new("Dancing")
 
aubrey.gifts #=> "Dancing"

```

Instances have a smaller scope they can be used in.
It may seem easy when reading about it, but in practicing it, it gets confusing at first.  It is important to know and get used to using the proper one at the proper time because of scope.   Since the names of some variables are common like:  
name, age, date, place, time, event   etc.…  If there used in their proper place the scopes won’t overlap.  If a programmer is years later, updating your code it should save problems and visa versa if your updating a programmer’s code it should be easier and cleaner. Scope is what it’s all about...

**More Examples:**

Inside of an instance method
In the code below, play is an instance method. It belongs to the object we created:  Cat.new. So self points to that object.

```
class Cat

  def play
    self
  end

end

c = Cat.new
c.play == c # => true

```
**Inside of a class method:**
For this example, play is a class method of Cat. With class methods, the class itself "owns" the method. self points to the class.

```
class Cat

  def self.play
    self
  end

end

Cat.play == Cat # => true
```



**Return values
In Ruby, a method always returns one object.
**

Nil is an object too, it means “nothing”, but it is still an object.  Surprised?

I was, I never looked at it that way before. 
The object returned could be the object nil, meaning “nothing”.   Also, in order to return a bunch of things we could return an Array, but the Array itself is just one object that holds a bunch of things.

Also, we do not have to use the statement return, as in other languages. In fact, a lot of Ruby code does not use most of the keywords at all.  We’ve used, puts, prints, return, or just the name of the method or value you want returned, but I think just the name, as` class_name.method_name or class_name or method_name` is the favorite. 
 
This is very convenient, but it is also something we need to learn, and there are other tricks to affect your outcome.  These are a few that affect what comes back on your screen:

1.	If we don’t do anything else, then a method will return the value that was returned from the last evaluated statement. 
2.	If we use “print”, We get no new line printed after our answer.
3.	If we use “puts”, it goes to a new line after our answer in the console, but it returns nil.  (mostly used for debugging)
4.	If we use “return” or just the name of the return value, you want. Its explicit.

There are times this will matter: 
You don’t want a list of things coming out like This,

```
Applebananapeachpearstrawberries etc.
```
You’d rather get your list like,

```
Apple
Banana
Peach
Pear
Strawberries etc.…
```

There are times depending on what your building, that you’ll need your return value to come back a certain way. " Puts" is handy it will return in the screen the correct answer, but the value always computes as nil.  There are times you’re not going to want that.  So" puts" is good for debugging.
If we just want to pass return values to other methods, we don't need any of the return keywords here, the last expression evaluated in a method becomes that method's return value.
Also, in certain cases, we do want to “return” from the method early, then we can still do this using the return statement. For now the purposes of this blog, we’ll leave that for later…


.
