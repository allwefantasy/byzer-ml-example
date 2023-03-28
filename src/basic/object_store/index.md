This tutorial shows how to use Byzer-lang to access Cloud Object Store.

1. Install object store plugin
2. Register object store FileSystem
3. Load/Save from the bucket

Before you start, you need to add the following configuration to the `.mlsql.config` file:

```
engine.spark.mlsql.path.schemas=oss,s3a,obs,abfs,abfss,wasbs,wasb,wasb
```

This configuration is used to allow the user to access the full path of the file with specific schema, such as `s3a://bucket_name/file_name`.

## 1. Install object store plugin

There are two ways to install the object store plugin.

1. Download plugin from https://download.byzer.org/byzer/misc/cloud and put the plugin in `$BYZER_HOME/plugin`. 
2. Using `!plugin` command. You will see the examples of this command in the notebooks.

## 2. Register object store FileSystem

The Datasource FS is used to register the object store information to the system.

Here is the code example.

```sql
load FS.``
Where `fs.s3a.endpoint`="s3.ap-northeast-1.amazonaws.com"
and `fs.s3a.bucket.BUCKET_NAME.access.key`="${s3a_ak}"
and `fs.s3a.bucket.BUCKET_NAME.secret.key`="${s3a_sk}"
and `fs.s3a.impl`="org.apache.hadoop.fs.s3a.S3AFileSystem"
and `fs.AbstractFileSystem.s3a.impl`="org.apache.hadoop.fs.s3a.S3A"
as output;
```

## 3. Load/Save from the bucket

Now you can load/save the data from the full bucket path.

