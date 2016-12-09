---
layout: page
title: Spark Closures
subtitle: Plus Other Functional Topics and Some Python Development Tools
---

Spark was built with Scala. Scala provides full support for functional programming and runs on the Java Virtual Machine. Functional programming in Python is its own topic, but we will very briefly cover some basics here that will be helpful.

Although data structures in Python are mutable. When working with RDDs through pySpark, data structures are immutable because RDDs are immutable. In general any Python data structure like dictionaries can be used with Spark, but they are required to be immutable even if Python implements them as a mutable data structure.

#### Lists

Lists in Python support map(), reduce() and filter(). Map applies a function to all the inputs. Reduce performs a computation on a list and returns the result. Filter returns a list of elements for which a function returns true.


#### Sets

Sets are unordered collections of unique values. Sets support union, intersection, difference, and some others. Sets can be created as immutable objects in Python using frozensets.


#### Anonymous Functions

Python implements anonymous functions using the lambda construct. Anonymous functions accept any number of inputs, but return just one value which can be another function, a value, or a data structure. We used anonymous functions several times in the Spark Shell examples. Here is a simple example of adding one.

{% highlight python %}
plusOne = lambda x: x+1
plusOne(1)
{% endhighlight %}

<br/>

#### Higher Order Functions

Higher-order functions accept functions as arguments and can return functions as a result. Map, reduce, and filter are higher order functions. Flatmap and reduceByKey, which we used in the Spark Shell examples are also higher-order functions.

+ A Callback function is a function that returns a function.
+ Tail calls are functions that call themselves.

<br/>

#### Closures

Closures in Python are conceptually identical to closures in Javascript. Closures are function objects that enclose the scope when they are instantiated and remember the values by enclosing the scope.

Spark automatically creates closures for functions that run on RDDs at workers and for any global variables used by those workers. When Transformations and Actions are performed using functions, Spark automatically sends a closure containing the function.


Having touched on the functional programming basics required for development, it is left as an exercise for the user to reference the areas required as needed. We are now going to add a couple development tools to help make it easier to develop Python applications with Spark, help rapidly build out Spark applications with Python, and allow us to visualize data results from Spark. We will then use these tools to build out a sample application. 


[Adding IPython and Jupyter](../jupyter_ipython)
