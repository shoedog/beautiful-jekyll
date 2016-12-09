---
layout: page
title: Python Driver
subtitle: Setup & Key Concepts
---

### Python Driver Program Setup

If you didn't add Spark to your path and set SPARK_HOME you will want to do so now. To launch a python driver you will need to call spark-submit which is in the spark/bin/ directory.  

{% highlight shell %}
:$ spark-submit <your-driver>.py
{% endhighlight %}

Below we have the minimal required setup for a Spark Application in Python:

{% highlight python %}
## Imports
from pyspark import SparkConf, SparkContext

## Shared variables and data
APP_NAME = "Spark Driver"

## Any Closure Functions

## Main
def main(sc):
    """
    RDD Transformation & Action descriptions
    """
    pass

if __name__ == "__main__":
    # Configure Spark
    conf = SparkConf().setAppName(APP_NAME)
    conf = conf.setMaster("local[*]")
    sc = SparkContext(conf=conf)

    # Execute main
    main(sc)
{% endhighlight %}


When we introduced Spark in the Spark Shell, it was mentioned that we needed to set the SparkConf() and SparkContext() in an application. We import those at the top and then configure them as the first executables when our main block starts. The use of the ifmain statement which defines the SparkContext and passes it to main allows the driver code to easily be imported into other Spark contexts, it also allows code to be imported into iPython/Jupyter or the pyspark shell to explore and analysis pieces of a dataset. The driver allows control over execution as sc.stop() for example can stop the program. Also, the local[*] field tells Spark to use as many processes as available so it can be developed locally but also scaled across a cluster.

We have introduced SparkConf, SparkContext, RDDs, and Transformations and Actions on RDDS. Before we build out a program, we should cover [Closures in Spark](../spark_closures).
