DISTINCT COUNT Multiple columns - https://github.com/prestodb/presto/issues/5281

The Hive connector has a hidden column $path (need to surround it in double quotes). 

Audit log
- https://github.com/zz22394/presto-audit

https://github.com/wyukawa/yanagishima

```
mvn versions:set -DnewVersion=0.167
mvn -N versions:update-child-modules

```
Raptor 
https://groups.google.com/forum/m/#!topic/presto-users/ni5yshI98K8

 Presto + HUE
- https://medium.com/@ilkkaturunen/integrating-presto-with-hue-61702b244839#.t6z8mxpdc

Export to CSV: https://groups.google.com/forum/#!msg/presto-users/kR-3YZAaNg8/5LXy4FfeT6cJ
```
presto --execute "select * from foo" --output-format CSV_HEADER > foo.csv

Use --output-format CSV_HEADER when running the CLI. Use --help to see all the options. Unfortunately, it doesn't list all the supported output formats:

ALIGNED
VERTICAL
CSV
TSV
CSV_HEADER
TSV_HEADER

```

http://teradata.github.io/presto/docs/141t/index.html

config.properties
```
http-server.log.path=/var/log/presto/http-request.log
http-server.log.max-size=67108864B
http-server.log.max-history=5
```

Presto-elasticsearch, https://github.com/albertocsm/presto


https://github.com/facebook/presto/issues/4182
https://github.com/facebook/presto/issues/4292
https://github.com/facebook/presto/issues/2060

com.facebook.presto.operator.PageTooLargeException: Remote page is too large

at com.facebook.presto.operator.HttpPageBufferClient.rewriteException(HttpPageBufferClient.java:465)

at com.facebook.presto.operator.HttpPageBufferClient.access$1400(HttpPageBufferClient.java:79)

at com.facebook.presto.operator.HttpPageBufferClient$1.onFailure(HttpPageBufferClient.java:346)

at com.google.common.util.concurrent.Futures$6.run(Futures.java:1310)

at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)

at java.util.concurrent.FutureTask.run(FutureTask.java:266)

at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.access$201(ScheduledThreadPoolExecutor.java:180)

at java.util.concurrent.ScheduledThreadPoolExecutor$ScheduledFutureTask.run(ScheduledThreadPoolExecutor.java:293)

at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)

at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)

at java.lang.Thread.run(Thread.java:745)

coordinator HA, 
{quote}
Search for "Service Inventory" in the group.

Two specific threads that I found useful were 
https://groups.google.com/forum/#!searchin/presto-users/service$20inventory/presto-users/guMk7IpO398/QBSNRV80MnMJ
https://groups.google.com/forum/#!searchin/presto-users/service$20inventory/presto-users/vUirVCZqaok/lVdq7Tq_Z2oJ
{quote}

checkstyle git@github.com:airlift/codestyle.git

https://github.com/prestodb/presto-jdbc-java6

Oracle Java 6:
http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html#jdk-6u45-oth-JPR

To configure Java 6 toolchain in ~/.m2/toolchains.xml put

<?xml version="1.0" encoding="UTF8"?>
<toolchains>
    <!-- JDK toolchains -->
    <toolchain>
        <type>jdk</type>
        <provides>
            <version>1.6</version>
            <vendor>sun</vendor>
        </provides>
        <configuration>
          <jdkHome>/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home/</jdkHome>
        </configuration>
    </toolchain>
</toolchains>


http://blogs.teradata.com/data-points/love-presto/