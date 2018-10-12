https://github.com/confluentinc/schema-registry/issues/707
```
{ "name": "foobar", "type": ["string", "null"], "default": null },
```
"default" -> https://avro.apache.org/docs/1.8.2/spec.html

https://issues.apache.org/jira/browse/AVRO-1811
```
{
      "name": "some_string",
      "doc": "a field that is guaranteed to compile to java.lang.String",
      "type": [
        "null",
        {
          "type": "string",
          "avro.java.string": "String"
        }
      ]
    },
```

https://www.ctheu.com/2017/03/02/serializing-data-efficiently-with-apache-avro-and-dealing-with-a-schema-registry/


https://www.ctheu.com/2017/01/18/how-to-communicate-between-micro-services-part-1/