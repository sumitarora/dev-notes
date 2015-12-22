data = [1, 2, 3, 4, 5]
data = ['a', 'b', 'c', 1, 2, 3]

>>> a1
[(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e')]



• union = combine two rdd's
• intersection = common elements
• subtract = diiference
• distinct = get distinct elements in set
• cartesian = all combinations of two sets
• zip = combine two rdd's


all elements = >>> a1.union(a2).collect()
[1, 2, 3, 4, 5, 'a', 'b', 'c', 1, 2, 3]

all unique elements = >>> a1.union(a2).distinct().collect()
['a', 1, 2, 'c', 3, 'b', 4, 5]

elements only in a = >>> a1.subtract(a1.intersection(a2)).collect()
[4, 5]

elements only in b = >>> a2.subtract(a1.intersection(a2)).collect()
['c', 'b', 'a']

common elements = >>> a1.intersection(a2).collect()
[1, 2, 3]

elements not common = >>> a1.union(a2).distinct().subtract(a1.intersection(a2)).collect()
['a', 'c', 'b', 4, 5]



sims.union(goldStandard).distinct().subtract(sims.intersection(goldStandard)).collect()

• map - done
• filter - done
• flatMap - done
• mapPartitions
• mapPartitionsWithIndex
• groupBy
• sortBy


• sample
• randomSplit


• union - done
• intersection - done
• subtract - done
• distinct - done
• cartesian - done
• zip - done


• keyBy
• zipWithIndex
• zipWithUniqueID
• zipPartitions
• coalesce
• repartition
• repartitionAndSortWithinPartitions • pipe


• reduce - done
• collect
• aggregate
• fold
• first
• take
• forEach
• top
• treeAggregate
• treeReduce
• forEachPartition • collectAsMap
• count
• takeSample
• max
• min
• sum
• histogram
• mean
• variance
• stdev
• sampleVariance
• countApprox
• countApproxDistinct
• takeOrdered
• saveAsTextFile
• saveAsSequenceFile
• saveAsObjectFile
• saveAsHadoopDataset
• saveAsHadoopFile
• saveAsNewAPIHadoopDataset
• saveAsNewAPIHadoopFile


amazonRecToToken = amazonSmall.map(lambda l: (l[0], tokenize(l[1])))
googleRecToToken = googleSmall.map(lambda l: (l[0], tokenize(l[1])))


idfsSmall = idfs(amazonRecToToken.union(googleRecToToken))
uniqueTokenCount = idfsSmall.count()


fullCorpusRDD = amazonFullRecToToken.union(googleFullRecToToken)
idfsFull = idfs(fullCorpusRDD)
idfsFullCount = idfsFull.count()
print 'There are %s unique tokens in the full datasets.' % idfsFullCount

# Recompute IDFs for full dataset
# idfsFullWeights = idfs(fullCorpusRDD)
# idfsFullBroadcast = sc.broadcast(idfsFullWeights)

# Pre-compute TF-IDF weights.  Build mappings from record ID weight vector.
amazonTokens = amazonFullRecToToken.flatMap(lambda l: l[1]).distinct()
print amazonTokens.count()

googleTokens = googleFullRecToToken.flatMap(lambda l: l[1]).distinct()
print googleTokens.count()

# amazonWeightsRDD = tfidf(amazonTokens,idfsFullBroadcast)
# googleWeightsRDD = tfidf(googleTokens,idfsFullBroadcast)
# print 'There are %s Amazon weights and %s Google weights.' % (amazonWeightsRDD.count(),
#                                                                googleWeightsRDD.count())



tfidf(tokens, idfs):


def idfs(corpus):
def tfidf(tokens, idfs):



val file = sc.textFile("/Users/sumitarora/Desktop/temp/gistfile1.txt");
http://stanford.edu/~rezab/sparkworkshop/slides/holden.pdf
https://spark-summit.org/wp-content/uploads/2015/03/SparkSummitEast2015-sample_slides.pdf
http://homepage.cs.latrobe.edu.au/zhe/ZhenHeSparkRDDAPIExamples.html
http://www.supergloo.com/fieldnotes/apache-spark-examples-of-transformations/#map

https://github.com/jspm/jspm-cli/blob/master/docs/getting-started.md

map()
val rows = records.map(_.split(','))
rows.take(5)

intersection()
cartesion()

flatMap()
// scala> sc.parallelize(List(1,2,3)).flatMap(x=>List(x,x,x)).collect
// res200: Array[Int] = Array(1, 1, 1, 2, 2, 2, 3, 3, 3)

// scala> sc.parallelize(List(1,2,3)).map(x=>List(x,x,x)).collect
// res201: Array[List[Int]] = Array(List(1, 1, 1), List(2, 2, 2), List(3, 3, 3))

distinct()
// distinct by ip address

pipe()

filter()
rows.filter(_(5) == "Female").count()
rows.filter(_(5) == "Male").count()

groupByKey()
// count by country
val pairsByCountry = rows.map(row => (row(4), 1))
val groupByCountry = pairsByCountry.groupByKey()

coalesce()

mapPartitions()

reduceByKey()

repartition()

mapPartitionsWithIndex()
//  List(x.next).iterator
val records = file.mapPartitionsWithIndex(
(i, iterator) =>
    if (i == 0 && iterator.hasNext) {
       iterator.next
       iterator
    } else iterator)

sortByKey()
// count by country and then sork by key and value

partitionBy()

sample()
rows.sample(true, 0.4).count()

join()
// split random and join

union()
// split random and take union

cogroup()

// src is your RDD
val noHeader = src.mapPartitionsWithIndex(
(i, iterator) =>
    if (i == 0 && iterator.hasNext) {
       iterator.next
       iterator
    } else iterator)




    val wordsList = List("cat", "elephant", "rat", "rat", "cat")
    val wordsRDD = sc.parallelize(wordsList, 5);
    wordsRDD.map(w => w + "s").collect()

    val pluralLengths = wordsRDD.map(w => w + "s").map(w => w.length).collect()
    val pairsRDD = wordsRDD.map(w => (w, 1)).collect()
    val wordsGrouped = pairsRDD.groupByKey()
    wordsGrouped.map( w => (w._1, sum(w._2)).collect()

    wordPairs.reduceByKey(lambda a,b: a + b)

    wordCountsCollected = (wordsRDD
                           .map(lambda word: (word, 1)) \
                           .reduceByKey(lambda x, y: x + y)
                           .collect())
    print wordCountsCollected
    uniqueWords = len(wordCountsCollected)

    from operator import add
    totalCount = (wordCounts
                  .map(lambda a: a[1])
                  .reduce(lambda a, b: a + b))
    average = totalCount / float(wordCounts.count())
    print totalCount
    print round(average, 2)

    return wordListRDD.map(lambda word: (word, 1)).reduceByKey(lambda x, y: x + y)

    top15WordsAndCounts = shakeWordsRDD.map(lambda w: (w, 1)).reduceByKey(lambda a,b: a + b).takeOrdered(15, key=lambda x: -x[1])


    // reading a file
    val file = spark.textFile("filepath")

    // finding lines containing keyword
    val lines = file.filter(line => line.contains("keyword"))
    val lines = file.filter(line => line.startsWoth("keyword"))
    val lines = file.filter(_.contains("keyword"))


    - read file
    val users = sc.textFile("/Users/sumitarora/workspace/LearningDataScience/dataset/movies/ml-100k/u.user")
    val movies = sc.textFile("/Users/sumitarora/workspace/LearningDataScience/dataset/movies/ml-100k/u.item")
    val ratings = sc.textFile("/Users/sumitarora/workspace/LearningDataScience/dataset/movies/ml-100k/u.data")

    - split data
    val usersData = users.map(_.split('|'))
    val moviesData = movies.map(_.split('|'))
    val ratingsData = movies.map(_.split('\t'))

    - total number of users
    usersData.count()

    - total number of males
    usersData.filter(_(2) == "M").count()


    - total numer of females
    usersData.filter(_(2) == "F").count()

    - count of males/females greater/less than age
    usersData.filter(_(2) == "F").filter(_(1).toInt < 20).count()

    usersData.map(_(2)).distinct().count()

    - average age of males

    - average age of females

    - range of ages by all/males/females

    - breakdown by occupation by all/males/females

    - breakdown by zip by all/males/females

    ratings.stats()


    rating_data = rating_data_raw.map(lambda line: line.split("\t"))
       ratings = rating_data.map(lambda fields: int(fields[2]))
       max_rating = ratings.reduce(lambda x, y: max(x, y))
       min_rating = ratings.reduce(lambda x, y: min(x, y))
       mean_rating = ratings.reduce(lambda x, y: x + y) / num_ratings
       median_rating = np.median(ratings.collect())
       ratings_per_user = num_ratings / num_users
       ratings_per_movie = num_ratings / num_movies
       print "Min rating: %d" % min_rating
       print "Max rating: %d" % max_rating
       print "Average rating: %2.2f" % mean_rating
       print "Median rating: %d" % median_rating
       print "Average # of ratings per user: %2.2f" % ratings_per_user
       print "Average # of ratings per movie: %2.2f" % ratings_per_movie

     user_ratings_grouped = rating_data.map(lambda fields: (int(fields[0]),
       int(fields[2]))).\
           groupByKey()


    user_ratings_byuser_local = user_ratings_byuser.map(lambda (k, v):
       v).collect()
       hist(user_ratings_byuser_local, bins=200, color='lightblue',
       normed=True)
       fig = matplotlib.pyplot.gcf()
       fig.set_size_inches(16,10)       





    parsed_logs, access_logs, failed_logs = parseLogs()

    # Calculate statistics based on the content size.
    content_sizes = access_logs.map(lambda log: log.content_size).cache()
    print 'Content Size Avg: %i, Min: %i, Max: %s' % (
        content_sizes.reduce(lambda a, b : a + b) / content_sizes.count(),
        content_sizes.min(),
        content_sizes.max())


    responseCodeToCount = (access_logs
                           .map(lambda log: (log.response_code, 1))
                           .reduceByKey(lambda a, b : a + b)
                           .cache())
    responseCodeToCountList = responseCodeToCount.take(100)


    labels = responseCodeToCount.map(lambda (x, y): x).collect()
    print labels
    count = access_logs.count()
    fracs = responseCodeToCount.map(lambda (x, y): (float(y) / count)).collect()
    print fracs

    hostCountPairTuple = access_logs.map(lambda log: (log.host, 1))
    hostSum = hostCountPairTuple.reduceByKey(lambda a, b : a + b)
    hostMoreThan10 = hostSum.filter(lambda s: s[1] > 10)
    hostsPick20 = (hostMoreThan10
                   .map(lambda s: s[0])
                   .take(20))
    print 'Any 20 hosts that have accessed more then 10 times: %s' % hostsPick20

    # Top Endpoints
    endpointCounts = (access_logs
                      .map(lambda log: (log.endpoint, 1))
                      .reduceByKey(lambda a, b : a + b))

    topEndpoints = endpointCounts.takeOrdered(10, lambda s: -1 * s[1])


    not200 = access_logs.filter(lambda log: log.response_code == 404)
    endpointCountPairTuple = not200.map(lambda log: (log.endpoint, 1))
    endpointSum = endpointCountPairTuple.reduceByKey(lambda a, b : a + b)
    topTenErrURLs = endpointSum.takeOrdered(10, lambda s: -1 * s[1])


    access_logs.map(lambda log: (log.host, log.date_time.day()))
    dayGroupedHosts = dayToHostPairTuple.groupByKey
    dayHostCount = dayGroupedHosts.map(lambda s: (s[0], count(s[1])))
    dailyHosts = dayHostCount.takeOrdered(lambda s: -1 * s[1]).cache()

    hosts = access_logs.map(lambda log: log.host))
    uniqueHosts = hosts.distinct()

    dayToHostPairTuple = access_logs.map(lambda log: (log.host, log.date_time.day()))

    dayGroupedHosts = dayToHostPairTuple.groupByKey()

    dayHostCount = dayGroupedHosts.<FILL IN>

    dailyHosts = (dayHostCount
                  <FILL IN>)
    dailyHostsList = dailyHosts.take(30)
    print 'Unique hosts per day: %s' % dailyHostsList


    print 'Top Ten Endpoints: %s' % topEndpoints

            host          = match.group(1),
            client_identd = match.group(2),
            user_id       = match.group(3),
            date_time     = parse_apache_time(match.group(4)),
            method        = match.group(5),
            endpoint      = match.group(6),
            protocol      = match.group(7),
            response_code = int(match.group(8)),
            content_size  = size


    draw graph
    import matplotlib.pyplot as plt

    def pie_pct_format(value):
        return '' if value < 7 else '%.0f%%' % value

    fig = plt.figure(figsize=(4.5, 4.5), facecolor='white', edgecolor='white')
    colors = ['yellowgreen', 'lightskyblue', 'gold', 'purple', 'lightcoral', 'yellow', 'black']
    explode = (0.05, 0.05, 0.1, 0, 0, 0, 0)
    patches, texts, autotexts = plt.pie(fracs, labels=labels, colors=colors,
                                        explode=explode, autopct=pie_pct_format,
                                        shadow=False,  startangle=125)
    for text, autotext in zip(texts, autotexts):
        if autotext.get_text() == '':
            text.set_text('')  # If the slice is small to fit, don't show a text label
    plt.legend(labels, loc=(0.80, -0.1), shadow=True)
    pass




    endpoints = (access_logs
                 .map(lambda log: (log.endpoint, 1))
                 .reduceByKey(lambda a, b : a + b)
                 .cache())
    ends = endpoints.map(lambda (x, y): x).collect()
    counts = endpoints.map(lambda (x, y): y).collect()

    fig = plt.figure(figsize=(8,4.2), facecolor='white', edgecolor='white')
    plt.axis([0, len(ends), 0, max(counts)])
    plt.grid(b=True, which='major', axis='y')
    plt.xlabel('Endpoints')
    plt.ylabel('Number of Hits')
    plt.plot(counts)
    pass



    dayToHostPairTuple = access_logs.map(lambda log: (log.date_time.day, log.host))

    dayGroupedHosts = dayToHostPairTuple.groupByKey()

    dayHostCount = dayGroupedHosts.map(lambda s: (s[0], len(set(s[1]))))

    dailyHosts = dayHostCount.sortBy(lambda s: s[0]).cache()




    dayAndHostTuple = access_logs.map(lambda log: (log.date_time.day, log.host))

    groupedByDay = dayAndHostTuple.groupByKey().map(lambda s: (s[0], len(s[1]) / len(set(s[1]))))

    sortedByDay = groupedByDay.sortBy(lambda s: s[0])

    avgDailyReqPerHost = sortedByDay

    avgDailyReqPerHostList = avgDailyReqPerHost.take(30)


    daysWithHosts = dailyHosts.map(lambda l: l[0]).collect()
    hosts = dailyHosts.map(lambda l: l[1]).collect()



    errDateCountPairTuple = badRecords.map(lambda r: (r.date_time.day, r.response_code)).groupByKey()

    errDateSum = errDateCountPairTuple.map(lambda s: (s[0], len(s[1])))

    errDateSorted = (errDateSum.sortBy(lambda s: s[0])).cache()



    Hands on Apache Spark - Part 1

    Loading file into apache spark
    val users = sc.textFile("/Users/sumitarora/workspace/LearningDataScience/dataset/movies/ml-100k/u.user")

    Data which is present in apache spark is list of users delimeted by new line and inofrmation of each users is further delimeted by | within each user. To perform any computation we must split user data for this we use map operation to split data.
    val usersData = users.map(_.split('|'))

    now to get the total number of users we just do
    - usersData.count()

    to get the total number of males / females we will use filter operation to filter our data and get result from that.
    usersData.filter(_(2) == "M").count()


    similarly we can get total numer of females
    usersData.filter(_(2) == "F").count()

    we can also apply multiple filters at the same time for eg. if we have to get males / females under a particular age. In this example I have take 20 as the age and looking for count of females under the age of 20
    - count of males/females greater/less than age
    usersData.filter(_(2) == "F").filter(_(1).toInt < 20).count()

    - average age of males
    usersData.filter(_(2) == "M").map(_(1).toInt).reduce( _ + _) / usersData.filter(_(2) == "M").count()

    - average age of females
    usersData.filter(_(2) == "F").map(_(1).toInt).reduce( _ + _) / usersData.filter(_(2) == "F").count()

    - range of ages by all/males/females

    - breakdown by occupation by all/males/females

    - breakdown by zip by all/males/females
