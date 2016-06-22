```
R에서 데이터베이스 또는 Presto, Phoenix에 접근하는 방법을 설명합니다.

== Presto ==
R / RPresto:
{{{
library('DBI')

con <- dbConnect(
  RPresto::Presto(),
  host='http://collector',
  port=8080,
  user=Sys.getenv('USER'),
  catalog='hive',
  schema='fdc'
)

res <- dbSendQuery(con, 'SELECT ts, fab, record_id, eqp_id, param_name from hive.fdc.fdc_eqp_trace_data limit 3')
# dbFetch without arguments only returns the current chunk, so we need to
# loop until the query completes.
while (!dbHasCompleted(res)) {
    chunk <- dbFetch(res)
    print(chunk)
}
}}}

== Phoenix ==
R / RJDBC:
{{{
options( java.parameters = "-Xmx8g" )
library(rJava)
library(RJDBC)
 
cp = c("/usr/lib/phoenix/phoenix-4.7.0-HBase-1.1-thin-client.jar")
.jinit(classpath=cp) 
 
drv <- JDBC("org.apache.phoenix.queryserver.client.Driver")
 
conn <- dbConnect(drv, "jdbc:phoenix:thin:url=http://collector:8765;serialization=PROTOBUF", "user", "password")
 
result <- dbGetQuery(conn, "SELECT DT,FAB,EQP,LOT_ID,OPERATION_ID,MODULE,RECIPE_ID,SLOT_ID,STEP_ID,UUID,CREATE_DTTS,END_TIME,
array_to_string(PARAM_NAME,':'),
array_to_string(MAX_VAL,':'),
array_to_string(MIN_VAL,':'),
array_to_string(MEAN_VAL,':'),
array_to_string(STDDEV_VAL,':'),
array_to_string(RANGE_VAL,':'),
array_to_string(MEDIAN_VAL,':'),
array_to_string(AREA_VAL, ':')
FROM HYNIX.BIG_TRACE_SUMMARY where dt='2016-05-16' LIMIT 20")
 
result
}}}

== Hive ==
Hive/RJDBC:
{{{
options( java.parameters = "-Xmx8g" )
library(rJava)
library(RJDBC)
 
cp = c("/usr/lib/hive/jdbc/hive-jdbc-2.0.1-standalone.jar", "/usr/lib/hadoop/client/hadoop-common.jar")
.jinit(classpath=cp) 
 
drv <- JDBC("org.apache.hive.jdbc.HiveDriver")
 
conn <- dbConnect(drv, "jdbc:hive2://collector:10000/fdc", "hive", "password")
 
result <- dbGetQuery(conn, "SELECT * from fdc.fdc_eqp_trace_data limit 2")
 
result


}}}

== 참고 ==
Install RPresto, RJDBC
{{{
-- offline install
# yum install libstdc++-devel

--  miniCRAN 을 이용한 local repository
https://github.com/RevolutionAnalytics/miniCRAN

-- R
> install.packages("miniCRAN")
> library("miniCRAN")
> pkgs <- c("RPresto", "httr", "stringi", "RCurl", "jsonlite", "stringi", "DBI", "methods", "rJava", "RJDBC")
> makeRepo(pkgDep(pkgs), path=file.path("/user/path", "miniCRAN"), download=TRUE)

 위와 같이 miniCRAN을 이용하여 repository를 구성하여 서버에 해당 디렉토리를 복사한다.

-- 대상 서버에서...
# export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/lib64/pkgconfig/
# /usr/bin/curl-config --libs 
-L/usr/lib64 -lcurl

# export LD_LIBRARY_PATH=/usr/java/latest/jre/lib/amd64/server:$LD_LIBRARY_PATH
# R CMD javareconf -e

-- R

stringi 설치를 위해 ...

$ wget http://www.ibspan.waw.pl/~gagolews/stringi/icudt55l.zip

# ls -als ~/miniCRAN/icudt55l.zip 
9940 -rw-r--r-- 1 sukbin games 10176327 2015-04-03 03:20 /root/miniCRAN/icudt55l.zip

# R

install.packages("rJava", 
                 repos = "file:///root/miniCRAN",
                 type = "source")

install.packages("RCurl", 
                 repos = "file:///root/miniCRAN",
                 type = "source")

install.packages("stringi", 
                 repos = "file:///root/miniCRAN",
                 type = "source",
                 configure.vars="ICUDT_DIR=/root/miniCRAN/")

pkgs <- c("RPresto", "RJDBC")
install.packages(pkgs, 
                 repos = "file:///root/miniCRAN",
                 type = "source")


}}}
```