# Intro to Spark #

**Starting Spark Shell**
```shell
% ./spark-shell                                                                      ✹ ✭
Spark assembly has been built with Hive, including Datanucleus jars on classpath
16/01/06 10:43:26 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 1.3.0
      /_/

Using Scala version 2.10.4 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_25)
Type in expressions to have them evaluated.
Type :help for more information.
Spark context available as sc.
SQL context available as sqlContext.

scala>
```
**Creating List RDD**

```shell
scala> val wordsList = List("cat", "elephant", "rat", "rat", "cat")
wordsList: List[String] = List(cat, elephant, rat, rat, cat)
```

**Map Example**
```shell
val wordsList = List("cat", "elephant", "rat", "rat", "cat")
val wordsRDD = sc.parallelize(wordsList, 5);
wordsRDD.map(w => w + "s").collect()
```

**Word Count Using GroupBy**
```shell
val pairsRDD = wordsRDD.map(w => (w, 1))
val wordsGrouped = pairsRDD.groupByKey()
wordsGrouped.map(w =>(w._1, w._2.sum)).collect()
```
**Reading a file**
```shell
val file = sc.textFile("/Users/sumitarora/workspace/pbrand/codesnippets/spark/basics.md")
```

**String Operations**
```shell
val lines = file.filter(line => line.contains("hello")) // Get lines containing word
val lines = file.filter(line => line.startsWoth("keyword")) // Get lines starting with the word
val lines = file.filter(_.contains("keyword")) // Get lines containing word
```
