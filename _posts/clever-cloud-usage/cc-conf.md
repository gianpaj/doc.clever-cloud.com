---
layout: page

id: cc_conf
parent: clever_cloud_usage
prev: billing
next: security 
---

#Configuration file

For every java or scala project using Maven, Ant or SBT, you need to write a small specific JSON file, copied at the root of your project. Make sure this file is called
**cc_conf.json**

This JSON is the configuration file that you will need for some deployments and builds. Here is the syntax:
{% highlight javascript%}
    {
        "build": {
            "type": "<string>",
            "goal": "<string>"
        },
        "deploy": {
            "jarName": "<string>",
            "goal": "<string>"
        }
    }
{% endhighlight %}


* "jarName" is a string containing the name of the main jar used to launch your application, with the extension.
* "build" is an object with the goal to execute.
* "deploy" is an object containing the type of deploy (Maven, Ant or SBT) and the goal to execute.

Example of cc_conf.json for a Maven deploy:

{% highlight javascript%}
    {
      "deploy": {
        "goal": "-Dtest.active=false assembly:jar-with-dependencies"
      }
    }

{% endhighlight %}

Example of cc_conf.json for Ant build:

{% highlight javascript%}
    {
      "build": {
        "type": "ant",
        "goal": "exterminate -Ddoctor.version=11"
      }
    }
{% endhighlight %}

Example of cc_conf.json for jar deploy:  

{% highlight javascript%}
    {
      "deploy": {
        "jarName": "Muad-dib.jar"	
      }
    }  
{% endhighlight %}