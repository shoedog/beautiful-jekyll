---
layout: page
title: IPython and Jupyter
subtitle: Adding More Python Development Tools for Spark
---

### Adding Some More Tools to Help Development

If you downloaded Anaconda during the setup section, you got IPython and Jupyter with it! These are highly recommended tools by the Python Spark development community. IPython can run the PySpark shell environment and Jupyter can be used to explore and visualize data. You can check your Anaconda install by typing the following:

{% highlight shell_session %}
:~$ python --version
{% endhighlight %}

You should see something like: `Python 3.5.2 :: Anaconda 4.2.0`. Now type: `jupyter notebook`. A browser window should open with a jupyter notebook. You can close the window and shut down the jupyter server in your terminal.

Run `jupyter notebook --generate-config` and open the _.jupyter/jupyter_notebook_config.py_ file. Append `c.NotebookApp.ip = '*'` at the top to configure Jupyter to listen on all ports. We can run Spark through IPython with the following command:

{% highlight shell_session %}
:~$ PYSPARK_DRIVER_PYTHON=ipython pyspark
{% endhighlight %}

Leave this running and open another terminal window. Now we can launch the jupyter notebook connected to our Spark instance:

{% highlight shell_session %}
:~$ PYSPARK_DRIVER_PYTHON=jupyter \
> PYSPARK_DRIVER_PYTHON_OPTS="notebook \
> --port=7777" pyspark --master local
{% endhighlight %}

In the top right click New and select a Python Environment. Type sc and either click the play icon or type CTRL-ENTER to run the cell.

You should see the following:
![SparkShell](../img/jupyter.png){:class="img-responsive"}

We can now use this development environment to rapidly prototype our Spark applications and quickly analyze our data in different ways. Jupyter provides many data visualization tools that are covered by other tutorials and are valuable in visualizing the results from analysis in Spark.

We will now use our fancy new development environment to develop an application, so leave it running.
[Sample Application](../sample)
