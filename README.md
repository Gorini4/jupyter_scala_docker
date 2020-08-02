# Docker Compose with Almond.sh core for Jupyter

1. Just `docker-compose up` and you're ready. 
2. Find link `http://127.0.0.1:8888/?token=xxxxxxxxxxxxxxxxxxxxxxxxxx` in docker logs. It will open Jupyter in your browser.
3. Create new notebook with core **Scala 2.12**.
4. Paste this code into the notebook and press *Shift + Enter*
``` Scala
import $ivy.`org.apache.spark::spark-sql:2.4.6`

import org.apache.log4j.{Level, Logger}
Logger.getLogger("org").setLevel(Level.OFF)

import org.apache.spark.sql._

val spark = {
  NotebookSparkSession.builder()
    .master("local[*]")
    .getOrCreate()
}
```
5. Now you can write your Spark code
``` Scala
val df = spark.read.csv("data.csv")
```
