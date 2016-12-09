---
layout: page
title: Setup
subtitle: Spark Setup with Python
---

Spark 2.0.2 works with Python 2.6+ or Python 3.4+. Anaconda is a Data Science platform powered by Python, with over 100 packages included. It also allows running multiple versions of Python in isolated environments. Download and install [Anaconda](https://www.continuum.io/downloads#all).   

Download and install Java 8:
{% highlight shell_session %}
:~$ sudo apt-get install software-properties-common
:~$ sudo add-apt-repository ppa:webupd8team/java
:~$ sudo apt-get update
:~$ sudo apt-get install oracle-java8-installer
{% endhighlight %}

Set the JAVA_HOME environment variable and ensure that Java is in your PATH.  

Download Apache Spark: We are using Release 2.0.2 released on November 14, 2014. Pre-built for Hadoop 2.7 or later.
You can download it here: [Spark](http://d3kbcqa49mib13.cloudfront.net/spark-2.0.2-bin-hadoop2.7.tgz)

Extract Spark, clean, and move the unzipped files into a new directory ~spark
{% highlight shell_session %}
:~$ tar -xf spark-2.0.2-bin-hadoop2.7.tgz
:~$ rm spark-2.0.2-bin-hadoop2.7.tgz
:~$ sudo mv spark-* spark
{% endhighlight %}

You need to set an environment variable for SPARK_HOME, and need to add SPARK_HOME to your PATH. If you are using Python3 you also need to set PYSPARK_PYTHON, but can skip this if you are using Python 2.7.
{% highlight shell %}
SPARK_HOME={Path to Spark}/spark
PATH=$SPARK_HOME/bin:$PATH
PYSPARK_PYTHON=python3
{% endhighlight %}

When setting environment variables and adding items to your path, you need to either open a new terminal or run the following:
{% highlight shell_session %}
:~$ source .<profile or env file>
{% endhighlight %}

Run Spark
If the environment variables and path were correctly set this will work in any directory:
{% highlight shell_session %}
:~$ pyspark
{% endhighlight %}
Otherwise you need to run PySpark from inside the spark directory you created.
{% highlight shell_session %}
:~$ cd spark
:spark$ ./bin/pyspark
{% endhighlight %}

You should see the following:
![SparkShell](../img/spark-shell.png){:class="img-responsive"}


We have Spark setup and now will explore the Spark Shell.
[Exploring the Spark Shell](../sparkshell)
