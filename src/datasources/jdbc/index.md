## JDBC

In this section, we will introduce how to use JDBC datasource in Byzer.

Before you start, you need to download the JDBC driver for the database you want to access. For example, if you want to access Oracle database, you need to download the Oracle JDBC driver. Then put the driver jar file in the `$BYZER_HOME/plugin` directory if you run byzer in local mode or the `$SPARK_HOME/libs` directory if you run Byzer in yarn mode.


Here is an MySQL example:

```sql
-- build connection info for mysql
connect jdbc where
driver="com.mysql.jdbc.Driver"
and url="jdbc:mysql://127.0.0.1:3306/wow?useSSL=false&haracterEncoding=utf8&zeroDateTimeBehavior=convertToNull&tinyInt1isBit=false"
and user="xxxx"
and password="xxxxx"
as mysql_instance;

-- load table from the mysql connection from above
load jdbc.`mysql_instance.vega_datasets` 
as mysql_vega_datasets;
```


Notice that Byzer load the data from database with JDBC protocal using only one thread by default. If you want to load the data from MySQL database using multiple threads, you can set the some parameters in the `load` statement.

The parameters for parallel loading are:

1. numPartitions
2. partitionColumn 
3. lowerBound
4. upperBound

Here is an example:

```sql

load jdbc.`mysql_instance.vega_datasets` 
where numPartitions="10"
and partitionColumn="id"
and lowerBound="1"
and upperBound="1000000"
as mysql_vega_datasets;

```

In this example, we set the "numPartitions" option to 10, which will split the data into 10 partitions by the id column which is specified by `partitionColumn` and load them in parallel. You can adjust the value of "numPartitions" to increase or decrease the degree of parallelism based on your specific needs and the available resources in your environment.

Note that the `partitionColumn` option must be a numeric or timestamp column. 

In order to ensure that the data is evenly distributed across partitions and to avoid issues with skewed data distribution, you also need to specify the lower and upper bounds of the partition column. The lower bound is the minimum value of the partition column, and the upper bound is the maximum value of the partition column. You can use the `min` and `max` functions to get the minimum and maximum values of the partition column.