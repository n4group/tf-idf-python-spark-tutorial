## Disclaimer

This tutorial is only for showcase and not recommended for production due no encription is used.

## Test

The following command starts a container with the Notebook server listening for HTTP connections on port 8888.
```
docker run -it --rm -p 8888:8888 -v $PWD/notebooks:/home/jovyan/work --name tf-idf jupyter/pyspark-notebook start-notebook.sh --NotebookApp.token=''
```

## Use

As best practice to save notebooks persistently run the container as a daemon so you don't have to CTRL+C to quit and can instead let docker handle the state.
```
docker run -td -p 8888:8888 -v $PWD/notebooks:/home/jovyan/work --name tf-idf jupyter/pyspark-notebook start-notebook.sh --NotebookApp.token=''
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

## Resources
* https://docs.docker.com/engine/installation/linux/linux-postinstall/#systemd
* http://maxmelnick.com/2016/06/04/spark-docker.html
* https://sparktutorials.github.io/2015/04/14/getting-started-with-spark-and-docker.html
* https://www.google.com/about/appsecurity/reward-program/
* https://security.googleblog.com/2017/03/vrp-news-from-nullcon.html
* https://futurezone.at/digital-life/spammer-panne-1-37-milliarden-datensaetze-im-web/250.265.208
* http://www.csoonline.com/article/3176433/security/spammers-expose-their-entire-operation-through-bad-backups.html
* https://github.com/jupyter/docker-stacks/tree/master/pyspark-notebook
* http://spark.apache.org/docs/latest/quick-start.html
* http://interactive.blockdiag.com/
* http://stackoverflow.com/questions/36756907/tensorflow-on-docker-how-to-save-the-work-on-jupyter-notebook
* https://spark.apache.org/docs/latest/mllib-feature-extraction.html
* https://spark.apache.org/docs/latest/ml-features.html#tf-idf
* https://spark.apache.org/docs/latest/ml-classification-regression.html
* https://www.wikidata.org/wiki/Wikidata:Database_download/de
