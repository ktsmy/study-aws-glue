# study-aws-glue

## 準備
see: https://docs.aws.amazon.com/ja_jp/glue/latest/dg/aws-glue-programming-etl-libraries.html#develop-local-scala

```
$ curl -O https://aws-glue-etl-artifacts.s3.amazonaws.com/glue-common/apache-maven-3.6.0-bin.tar.gz
$ tar zxvf apache-maven-3.6.0-bin.tar.gz -C /path/to/maven

$ curl -O https://aws-glue-etl-artifacts.s3.amazonaws.com/glue-1.0/spark-2.4.3-bin-hadoop2.8.tgz
$ tar zxvf spark-2.4.3-bin-hadoop2.8.tgz -C /path/to/spark
$ export SPARK_HOME=/path/to/spark/spark-2.4.3-bin-spark-2.4.3-bin-hadoop2.8

$ export PATH=/path/to/maven/apache-maven-3.6.0/bin:$SPARK_HOME/bin:$PATH
```

## 実行

Spark shellを使う場合
```
$ spark-shell
```

コードをコンパイルして実行する場合
```
$ mvn package
$ mvn exec:java -Dexec.mainClass="HelloWorld" -Dexec.args="--JOB-NAME HelloWorld"
$ mvn exec:java -Dexec.mainClass="SparkSample" -Dexec.args="--JOB-NAME SparkSample"

# AWSと接続する場合は必要な環境変数を設定する
$ export AWS_REGION=ap-northeast-1
$ export AWS_ACCESS_KEY_ID=xxxxx
$ export AWS_SECRET_ACCESS_KEY=yyyyy
$ export AWS_SESSION_TOKEN=zzzzz
$ mvn exec:java -Dexec.mainClass="GlueSample" -Dexec.args="--JOB-NAME GlueSample"
$ mvn exec:java -Dexec.mainClass="GlueAwsSdkSample" -Dexec.args="--JOB-NAME GlueAwsSdkSample"
```

