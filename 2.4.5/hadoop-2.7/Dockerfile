FROM bsolomon1124/scala:2.11.12
# "Note that, Spark is pre-built with Scala 2.11 except version 2.4.2, which is pre-built with Scala 2.12."

ENV SPARK_VERSION 2.4.5
ENV HADOOP_VERSION 2.7
ENV SPARK_HOME '/usr/src/spark'
ENV PATH "${SPARK_HOME}/bin:$PATH"

RUN set -ex \
    && export GNUPGHOME="$(mktemp -d)" \
    && wget -O spark.tar.gz "https://mirrors.ocf.berkeley.edu/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz" \
    && wget -O spark.asc "https://downloads.apache.org/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz.asc" \
    && gpg --batch --keyserver pgpkeys.mit.edu --recv-key EDA00CE834F0FC5C \
    && gpg --batch --verify spark.asc spark.tar.gz \
    && { command -v gpgconf > /dev/null && gpgconf --kill all || :; } \
    && mkdir -p /usr/src/spark/ \
    && tar -xzv -C /usr/src/spark --strip-components=1 -f spark.tar.gz \
    && rm -rf "$GNUPGHOME" spark.asc spark.tar.gz \
    && ln -s "${SPARK_HOME}/bin/spark-shell" /usr/local/bin/spark-shell \
    && ln -s "${SPARK_HOME}/bin/pyspark" /usr/local/bin/pyspark

CMD ["spark-shell"]

