---
layout: post
title:      "The use of Self in Ruby & Initializing instance variables  & Return Values"
date:       2020-02-02 15:12:31 -0500
permalink:  the_use_of_self_in_ruby_and_initializing_instance_variables_and_return_values
---


Before I started this blog, I thought that self was mostly used for the Classes and Modules.   See I was more focased on Class methods.  Now I see there are alot of both.  And its importiant to be clear on both.    Let’s start at the beginning though….

**What is Self?**
Self in Ruby gives you access to the current Object.  The objec that’s using Self in the top of the name, like this is, calling it on a Class.  So Self is a special variable that Ruby uses to  represent a way to reference a class or and instance of the class without explicitly naming the class or instance, therefore increasing your abstractness of your code allowing it to be cleaner and more flexible. 

**Code below:** Bark belongs to the object i created.(Dog.new).  Bark is an instance method.  So self points to that object.
```
class Dog
   
	  def bark
	    self
	  end
end

d = Dog.new
d.bark == d #=> true


```

**Code Below:** Bark is a class method of Dog.  Self points to the class. The class itself owns the method.
```

class Dog

     def self.bark
        self
     end
end

Dog.bark  == Dog #=>   true  
```

**To Explain:**
A method call in Ruby is the sending of a message to a receiver. It means that every piece of code you write is called on some object.
So, if you're new to coding, start asking yourself “What am I calling this method on?". "Am I calling it on the entire class or an instance of the class?"

Self is a set apart variable in Ruby that points to the object that "owns" the currently executing code.
This seems straight forward unless your new at it.  But its importiant, so take the time to get it straight.

 Ruby uses self everywhere so its good to get used to telling yourself when it’s an instance of the method or the Class method itself?
Ruby also lets you show the difference in Class variables by using one or two @ signs like this:
```
@name       is Instance variables
@@name     is Class variables
```






**Initializing Instances:**
 
You can initialize an instance like this, we’re creating an instance of a new child.
Here were using setter and getter methods to be creating a new instance of the Child class. `
```
class Child
  def initialize(name)
	  @name = name
  end
 
  def name=(name)
	  @name = name
  end
 
  def name
    @name
  end
end
```

**We can use an initialize method, like this:**
```
class Child

      def initialize(name, gifts)
           @name = name
           @gifts = gifts
      end
	
end
```
**Now, we can call a new instance like this:**


```
aubrey = Child.new("Aubrey", "Dancing")

aubrey.name #=> "Aubrey"

 aubrey.gifts #=> "Dancing"

```
**Instance variables**
They always refer to the invocation object. They are always visible in all methods of the class. They always refer to the i object being invoked. 

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

There are times depending on what your building, that you’ll need your return value to come back a certain way. " Puts" is handy it will display in the screen, but the value always computes as nil.  There are times you’re not going to want that.  So" puts" is good for debugging.
If we just want to pass return values to other methods, we don't need any of the return keywords here, the last expression evaluated in a method becomes that method's return value.
Also, in certain cases, we do want to “return” from the method early, then we can still do this using the return statement. For now the purposes of this blog, we’ll leave that for later…


.
