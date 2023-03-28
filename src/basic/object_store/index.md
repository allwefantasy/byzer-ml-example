This tutorial shows how to use Byzer-lang to access Cloud Object Store.

1. Install object store plugin
2. Register object store FileSystem
3. Load/Save from the bucket

Before you start, you need to add the following configuration to the `.mlsql.config` file:

```
engine.spark.mlsql.path.schemas=oss,s3a,obs,abfs,abfss,wasbs,wasb,wasb
```

This configuration is used to allow the user to access the full path of the file with specific schema, such as `s3a://bucket_name/file_name`.