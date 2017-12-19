# Hadoop Sequence Parser (HSP)

**Hadoop Sequence Parser (HSP)** is a Java library that allows to parse DNA/RNA sequence reads from FASTQ/FASTA datasets stored on the Hadoop Distributed File System (HDFS).

HSP supports the processing of input datasets compressed with Gzip (i.e., .gz extension) and BZip2 (i.e., .bz2 extension) codecs. However, when considering compressed data that will be later processed by Hadoop or any other data processing engine (e.g., Spark), it is important to understand whether the underlying compression format supports splitting, as many codecs need the whole input stream to uncompress successfully. On the one hand, Gzip does not support splitting and HSP will not split the gzipped input dataset. This will work, but probably at the expense of performance. On the other hand, BZip2 does compression on blocks of data and later these compressed blocks can be decompressed independent of each other, so it does support splitting. Therefore, BZip2 is the recommended codec to use with HSP for best performance.

## Getting Started

### Prerequisites

* Make sure you have Java Develpment Environment (JDK) version 1.6 or above

* Make sure you have a working Apache Maven distribution version 3 or above
  * See https://maven.apache.org/install.html

### Installation

In order to compile, build and install the JAR distribution in your Maven local repository, just execute the following Maven command from within the HSP root directory:

```
$ mvn install
```
### Usage

In order to use the HSP library in your projects, add the following Maven dependency in your pom file:

```xml
<dependency>
  <groupId>es.udc.gac</groupId>
  <artifactId>hadoop-sequence-parser</artifactId>
  <version>1.0</version>
</dependency>
```

## Authors

* **Roberto R. Expósito** (http://gac.udc.es/~rreye)
* **Luis Lorenzo Mosquera** (https://github.com/luislorenzom)
* **Jorge González-Domínguez** (http://gac.udc.es/~jgonzalezd)

## License

This library is distributed as free software and is publicly available under the GPLv3 license (see the [LICENSE](LICENSE) file for more details)
