HiveServer2 Web UI:
- http://hostname:10002
- https://issues.apache.org/jira/browse/HIVE-12338
- http://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_hive_webui.html

Hive / Tez:
- Hive CLI / beeline:
```
set hive.execution.engine=tez;
set tez.que.name=root.default;

SELECT ...
```
- Hive JDBC:
```
jdbc:hive2://ichbig-01-002:10000?hive.execution.engine=tez;tez.queue.name=root.default
```

​https://streever.atlassian.net/wiki/display/HADOOP/Hive+Performance+Tips

ORC:
- https://streever.atlassian.net/wiki/display/HADOOP/Optimizing+ORC+Files+for+Query+Performance