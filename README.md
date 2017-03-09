## Motivation
Why Spark?

[Apache Spark](https://spark.apache.org/) is a fast and general engine for large-scale data processing.

## Test

The following command starts a container with the Notebook server listening for HTTP connections on port 8888.
```
docker run -it --rm -p 8888:8888 \
  -v $PWD/notebooks:/home/jovyan/work \
  --name tf-idf jupyter/pyspark-notebook start-notebook.sh --NotebookApp.token=''
```

## Use

As best practice to save notebooks persistently run the container as a daemon so you don't have to CTRL+C to quit and can instead let docker handle the state.
```
docker run -td -p 8888:8888 \
  -v $PWD/notebooks:/home/jovyan/work \
  --name tf-idf jupyter/pyspark-notebook start-notebook.sh --NotebookApp.token=''
```

# Stop
```
docker stop tf-idf
```

# Start
```
docker start tf-idf
```

# Remove
Remove docker container.
```
docker rm tf-idf
```

## Disclaimer

This tutorial is only for showcase and not recommended for production due no encription is used.


## Content

# TF-IDF

```python
from pyspark.mllib.feature import HashingTF, IDF

#documents

hashingTF = HashingTF()
tf = hashingTF.transform(documents)

tf.cache()
idf = IDF().fit(tf)
tfidf = idf.transform(tf)

idfIgnore = IDF(minDocFreq=2).fit(tf)
tfidfIgnore = idfIgnore.transform(tf)
```

## Resources

# Docker

* [Documentation](https://docs.docker.com/) - Get Started
* [Linux post install steps](https://docs.docker.com/engine/installation/linux/linux-postinstall/#systemd)
* [pyspark-notebook](https://hub.docker.com/r/jupyter/pyspark-notebook/) - containerized dependencies (spark, python, ...)
* [Blog Post](http://maxmelnick.com/2016/06/04/spark-docker.html) - Blog post about pyspark-notebook

# Spark
* [Apache Spark](https://spark.apache.org/)
* [Quick Start](http://spark.apache.org/docs/latest/quick-start.html)
* [TF-IDF](https://spark.apache.org/docs/latest/mllib-feature-extraction.html#tf-idf) - ML library

# Wikidata
* [Dumps](https://www.wikidata.org/wiki/Wikidata:Database_download/de)
