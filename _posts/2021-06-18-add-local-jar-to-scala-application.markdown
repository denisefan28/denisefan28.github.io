---
layout: post
title:  "Load GraphFrame jar into Scala Application"
date:   2021-06-18 17:00:26 +0800
categories: Spark, GraphX
---

# GraphX to GraphFrame
GraphX is to RDD just as GraphFrame to DataFrame.Based on this fact,we started to consider moving existing code using GraphFrame instead of GraphX.

GraphFrame is an external package not natually included in the spark library.
In the official document of GrameFrame, it demonstrated how to use spark-shell, which is an interactive way, by adding `--packages` argument to download spark packages and dependencies automatically.

```shell

spark-shell --master local[4] --jars ~/project/lib/graphframes-0.8.0-spark2.4-s_2.11.jar

```

If we wanna use SBT and deploy our code as a jar packge to run on the dataplatform. Seveal steps are recommended below:

- 1. Choose the right GraphFrame version
we need to first down GraphFrame jar from [Spark Package][spark-package]
Then move the jar to our projects' library path.
After start sbt server, tyep command `show unmanagedBase`, it will show this path of GraphFrame jar.

- 2.Add jar to local classpath
First consider using `inspect <setting-key>`, this command will displays information about settings, such as the value, description, defining scope, dependencies, delegation chain, and related settings.
After `inspect fullClasspath` and `show fullClasspath`, make sure GraphFrame package are located under one of the displayed directory.

Finally, using `compile` to check GraphFrame jar is sucessfully loaded.

[spark-package]: https://spark-packages.org/package/graphframes/graphframes
[grahframe-git]: https://github.com/graphframes/graphframes
