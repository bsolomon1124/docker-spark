# Docker Spark Image

Disclaimer: this image's size is about 806MB.
I cannot make it much smaller; Spark is a large binary.

Usage:

```bash
docker container run -it --rm bsolomon1124/spark:2.4.5-hadoop2.7
```

This will start a `spark-shell`, Spark 2.4.5 / Hadoop 2.7 / Scala 2.11.12.
