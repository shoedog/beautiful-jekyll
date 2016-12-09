---
layout: page
title: Spark Shell
subtitle: Spark Shell Basics
---


We are going to explore some of the basics of the Spark API in the Spark Shell. In the following examples, Spark Shell examples will have `>>>` pre-pended and non-spark shell examples will have `:~$` prepended. Otherwise the example can be assumed as output from the Spark Shell unless stated otherwise.

The following command displays available options in the Spark Shell:
{% highlight shell %}
:~$ pyspark --help
{% endhighlight %}
<br/>

---  

### SparkContext

First, lets view the [Spark Context](http://spark.apache.org/docs/latest/api/python/pyspark.html#pyspark.SparkContext). Type the following into the Spark Shell.

{% highlight shell %}
 >>> sc
{% endhighlight %}

You should see something like this:
{% highlight shell %}
 <pyspark.context.SparkContext object at 0x101c2de80>
{% endhighlight %}

The SparkContext object tells Spark how to access a cluster. It is the main entry point for Spark functionality. SparkContext is like _Highlander_ in that there can be only one per cluster. To create a new SparkContext, the active SparkContext must be stopped. In the shell, SparkContext is instantiated automatically. SparkContext must be created as the first step in any Spark program. SparkContext is created from a [_SparkConf_ object](http://spark.apache.org/docs/latest/api/python/pyspark.html#pyspark.SparkConf). We will create a program later using SparkConf instead of relying on the automatically created version from the shell.

##### Uses of the SparkContext object include:
* creating RDDs  
* creating accumulators  
* creating broadcast variables for the cluster  
* accessing Spark services  
* running jobs  

In the shell we cannot make our own SparkContext, but can modify the master that the instance connects to, add files to the runtime path, add dependencies.

___  

### SparkSession

If we enter `spark` into the shell, we will see the [SparkSession Object](http://spark.apache.org/docs/latest/api/python/pyspark.sql.html#pyspark.sql.SparkSession).

{% highlight shell %}
 >>> spark
{% endhighlight %}

SparkSession is the entry point to Spark SQL. It is the first object after SparkContext that needs to be created when developing Spark SQL applications. In the SparkShell, SparkSession is also automatically instantiated.

[Let's learn more about using the Shell with Resilient Distributed Datasets](../rdd)
