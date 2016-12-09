---
layout: page
title: RDD
subtitle: Resilient Distributed Dataset
---

### RDD (Resilient Distributed Dataset)

The primary data abstraction provided by Spark is the RDD ( _Resilient Distributed Dataset_ ). Spark defines them as a:  

> fault-tolerant collection of elements that can be operated on in parallel.

The RDD is designed to be able to recover from failures and to split large datasets into chunks to be processed in at the same time on distributed nodes.

Create an RDD in one of two ways: parallelize existing collection or referencing an external dataset.

To create a RDD from an external dataset, Spark can use any storage source support by Hadoop which include text, key-value, fixed-length,
n number of lines, sequence files for binary, and database input. [Hadoop Inputs](https://hadoop.apache.org/docs/current/api/org/apache/hadoop/mapreduce/class-use/InputFormat.html)

We can get a textfile from [textfiles.com](http://www.textfiles.com/100/) if you don't have one handy. I downloaded this one [adventur](http://www.textfiles.com/100/adventur.txt). Once you have downloaded the .txt file in your working directory, we will run some 'hello-world' commands with the file.

{% highlight shell %}
 >>> text = sc.textFile("adventur.txt")
 >>> text.count()
 132
 >>> text.first()
 ''
 >>> text.take(30)
 >>> text.takeOrdered(30)
 >>> text.countByValue()
{% endhighlight %}

The .textFile() method creates an RDD from a textfile. We also used some _Actions_ supported by Spark. Actions return values. Count returns the number of items in the RDD, first returns the first item, take returns the first N items, takeOrdered returns the first N items sorted in ascending order, countByValue returns the count of each unique value.

RDDs are operated on with _actions_ as well as _transformations_. Transformations return pointers to new RDDs. Lets try a couple.

{% highlight shell %}
 >>> linesWithNow = text.filter(lambda line: "NOW" in line)
 >>> linesWithNow.count()
 29
 >>> linesWithMostWords = text.map(lambda line: len(line.split())).reduce(lambda a, b: a if (a > b) else b)
 >>> linesWithMostWords
 17
 >>> wordCounts = text.flatMap(lambda line: line.split()).map(lambda word: (word, 1)).reduceByKey(lambda a, b: a+b)
 >>> wordCounts.collect()
{% endhighlight %}

Congratulations, you just ran a map-reduce! The transformation for linesWithNow should be straightforward as filter returns any line that contains "NOW". For linesWithMostWords each line is mapped to an integer value in the first transformation. The second transformation reduce returns the line that has the most words. The map and reduce transformations were chained here. We likewise could have chained filter().count() in the linesWithNow example.

For wordcounts, we use flatMap which maps each input to 0 or more outputs, so each line is applied to 0 or more words in the line when we call map. The call to map sets each word as a unique key passed to reduceByKey. reduceByKey then aggregates words that are the same. collect returns all the elements as an array.


A simple example using an existing collection to create a RDD instead of referencing an external dataset:
{% highlight shell %}
 >>> data = [1, 2, 3, 4, 5]
 >>> distdata = sc.parallelize(data)
 >>> distData.reduce(lambda a, b: a + b)
{% endhighlight %}

Once a Parallelized Collection is created, it can be operated on. The reduce method above sums the list elements.

---

#### RDD Operations  

To review, there are two types of operations on RDDs:

+ **_transformations:_**  
Create a new dataset from an existing one. [Common transformations](http://spark.apache.org/docs/latest/programming-guide.html#transformations)
+ **_actions:_**  
Return a value to the driver after running a computation on the dataset. [Common actions](http://spark.apache.org/docs/latest/programming-guide.html#actions)


Transformations only are computed when an action requires a result to return to the driver. By default, each transform is recomputed each time an action is run, but can be persisted in memory using the <em>persist</em> or the <em>cache</em> method.

![SparkShell](../img/action_transform.png){:class="img-responsive"}


[It's time to create a Python Driver Program](../python_driver)
