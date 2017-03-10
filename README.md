# Motivation

Lets process wikidata. Then why Spark?

[Apache Spark](https://spark.apache.org/) is a fast and general engine for large-scale data processing.

## Spark
* [Apache Spark](https://spark.apache.org/)
* [Quick Start](http://spark.apache.org/docs/latest/quick-start.html)
* [TF-IDF](https://spark.apache.org/docs/latest/mllib-feature-extraction.html#tf-idf) - ML library

## Wikidata
* [Dumps](https://www.wikidata.org/wiki/Wikidata:Database_download/en)

# Installation

## Docker

* [Documentation](https://docs.docker.com/) - Get Started
* [Linux post install steps](https://docs.docker.com/engine/installation/linux/linux-postinstall/#systemd)
* [pyspark-notebook](https://hub.docker.com/r/jupyter/pyspark-notebook/) - containerized dependencies (spark, python, ...)
* [Blog Post](http://maxmelnick.com/2016/06/04/spark-docker.html) - Blog Post about pyspark-notebook


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

## Stop
```
docker stop tf-idf
```

## Start
```
docker start tf-idf
```

## Remove
Remove docker container.
```
docker rm tf-idf
```

## Disclaimer

This tutorial is only for showcase and not recommended for production due no encription is used.



# Notebooks

* [Get Started: count](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/count.ipynb) - Count Wikidata Rows
* [process Wikidata](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/wikidata_as_inlined_json_subset.ipynb) - Extract a tiny wikidata subset for testbed
* [page sample](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/sample_wikidata_json.ipynb) - sample JSON Object of a wiki page
* [JSON schema](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/json_schema.ipynb) - Get the JSON schema from subset
* [processing JSON](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/reduce_json.ipynb) - Process wikidata subset (get label and description)
* [TF-IDF](https://github.com/n4group/tf-idf-python-spark-tutorial/blob/master/notebooks/reduce_json.ipynb) - Build a search engine by wiki page descriptions with TF-IDF


# TF-IDF

Code snippet from Apache Spark documentation [TF-IDF](https://spark.apache.org/docs/latest/mllib-feature-extraction.html#tf-idf)

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

## License

MIT © [n4group](https://github.com/n4group)
