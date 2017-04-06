Hive 2.1.1 & MSSQL
- https://issues.apache.org/jira/browse/HIVE-16106
 
Hive LLAP:
- https://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.5.0/bk_command-line-installation/content/llap_install_unsecure.html
- http://eastcirclek.blogspot.kr/2016/10/how-to-start-hive-llap-functionality.html

https://community.hortonworks.com/questions/4343/what-is-the-best-approach-for-migrating-no-data-lo.html


# HiveServer2 Web UI
- http://hostname:10002
- https://issues.apache.org/jira/browse/HIVE-12338
- http://www.cloudera.com/documentation/enterprise/latest/topics/cm_mc_hive_webui.html

# Hive / Tez
- Hive CLI / beeline:
```
set hive.execution.engine=tez;
set tez.queue.name=root.default;

SELECT ...
```
- Hive JDBC:
```
jdbc:hive2://ichbig-01-002:10000?hive.execution.engine=tez;tez.queue.name=root.default
```

​https://streever.atlassian.net/wiki/display/HADOOP/Hive+Performance+Tips

# ORC
- https://streever.atlassian.net/wiki/display/HADOOP/Optimizing+ORC+Files+for+Query+Performance