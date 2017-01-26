```
diff --git a/bigtop-packages/src/common/hive/do-component-build b/bigtop-packages/src/common/hive/do-component-build
index 2293c55..6e65494 100644
--- a/bigtop-packages/src/common/hive/do-component-build
+++ b/bigtop-packages/src/common/hive/do-component-build
@@ -20,19 +20,17 @@ set -ex
 
 HIVE_MAVEN_OPTS=" -Dhbase.version=$HBASE_VERSION \
 -Dzookeeper.version=$ZOOKEEPER_VERSION \
--Dhadoop.mr.rev=23 \
--Dhadoop.security.version=$HADOOP_VERSION \
--Dhadoop-23.version=$HADOOP_VERSION \
--Dhbase.hadoop2.version=$HBASE_VERSION \
--Dmvn.hadoop.profile=hadoop23 \
+-Dhadoop.version=$HADOOP_VERSION \
 -DskipTests \
--Dhbase.version.with.hadoop.version=$HBASE_VERSION \
 -Dtez.version=${TEZ_VERSION} \
 -Dspark.version=${SPARK1_VERSION}
 "
 
 export MAVEN_OPTS="-Xmx1500m -Xms1500m -XX:MaxPermSize=256m"
-mvn ${HIVE_MAVEN_OPTS} clean install -Phadoop-2,dist "$@"
+mvn ${HIVE_MAVEN_OPTS} clean install -Pdist "$@"
 
 mkdir -p build/dist
 tar -C build/dist --strip-components=1 -xzf packaging/target/apache-hive-${HIVE_VERSION}-bin.tar.gz
+
+# HIVE-13177 
+sed -i "s#jdbcStandaloneJarPath=\`ls \${HIVE_LIB}/hive-jdbc-\*-standalone.jar\`#jdbcStandaloneJarPath=#" build/dist/bin/ext/beeline.sh
diff --git a/bigtop-packages/src/common/hive/patch0.diff b/bigtop-packages/src/common/hive/patch0.diff
deleted file mode 100644
index d70e694..0000000
--- a/bigtop-packages/src/common/hive/patch0.diff
+++ /dev/null
@@ -1,228 +0,0 @@
-diff --git a/pom.xml b/pom.xml
-index 3c0bc9b..9bbee65 100644
---- a/pom.xml
-+++ b/pom.xml
-@@ -157,7 +157,7 @@
-     <ST4.version>4.0.4</ST4.version>
-     <tez.version>0.5.2</tez.version>
-     <super-csv.version>2.2.0</super-csv.version>
--    <spark.version>1.3.1</spark.version>
-+    <spark.version>1.5.1</spark.version>
-     <scala.binary.version>2.10</scala.binary.version>
-     <scala.version>2.10.4</scala.version>
-     <tempus-fugit.version>1.1</tempus-fugit.version>
-diff --git a/ql/src/java/org/apache/hadoop/hive/ql/exec/spark/status/impl/JobMetricsListener.java b/ql/src/java/org/apache/hadoop/hive/ql/exec/spark/status/impl/JobMetricsListener.java
-index 51772cd..52f4b9c 100644
---- a/ql/src/java/org/apache/hadoop/hive/ql/exec/spark/status/impl/JobMetricsListener.java
-+++ b/ql/src/java/org/apache/hadoop/hive/ql/exec/spark/status/impl/JobMetricsListener.java
-@@ -23,29 +23,15 @@
-
- import org.apache.commons.logging.Log;
- import org.apache.commons.logging.LogFactory;
-+import org.apache.spark.JavaSparkListener;
- import org.apache.spark.executor.TaskMetrics;
--import org.apache.spark.scheduler.SparkListener;
--import org.apache.spark.scheduler.SparkListenerApplicationEnd;
--import org.apache.spark.scheduler.SparkListenerApplicationStart;
--import org.apache.spark.scheduler.SparkListenerBlockManagerAdded;
--import org.apache.spark.scheduler.SparkListenerBlockManagerRemoved;
--import org.apache.spark.scheduler.SparkListenerEnvironmentUpdate;
--import org.apache.spark.scheduler.SparkListenerExecutorMetricsUpdate;
--import org.apache.spark.scheduler.SparkListenerJobEnd;
- import org.apache.spark.scheduler.SparkListenerJobStart;
--import org.apache.spark.scheduler.SparkListenerStageCompleted;
--import org.apache.spark.scheduler.SparkListenerStageSubmitted;
- import org.apache.spark.scheduler.SparkListenerTaskEnd;
--import org.apache.spark.scheduler.SparkListenerTaskGettingResult;
--import org.apache.spark.scheduler.SparkListenerTaskStart;
--import org.apache.spark.scheduler.SparkListenerUnpersistRDD;
--import org.apache.spark.scheduler.SparkListenerExecutorRemoved;
--import org.apache.spark.scheduler.SparkListenerExecutorAdded;
-
- import com.google.common.collect.Lists;
- import com.google.common.collect.Maps;
-
--public class JobMetricsListener implements SparkListener {
-+public class JobMetricsListener extends JavaSparkListener {
-
-   private static final Log LOG = LogFactory.getLog(JobMetricsListener.class);
-
-@@ -54,36 +40,6 @@
-   private final Map<Integer, Map<String, List<TaskMetrics>>> allJobMetrics = Maps.newHashMap();
-
-   @Override
--  public void onExecutorRemoved(SparkListenerExecutorRemoved removed) {
--
--  }
--
--  @Override
--  public void onExecutorAdded(SparkListenerExecutorAdded added) {
--
--  }
--
--  @Override
--  public void onStageCompleted(SparkListenerStageCompleted stageCompleted) {
--
--  }
--
--  @Override
--  public void onStageSubmitted(SparkListenerStageSubmitted stageSubmitted) {
--
--  }
--
--  @Override
--  public void onTaskStart(SparkListenerTaskStart taskStart) {
--
--  }
--
--  @Override
--  public void onTaskGettingResult(SparkListenerTaskGettingResult taskGettingResult) {
--
--  }
--
--  @Override
-   public synchronized void onTaskEnd(SparkListenerTaskEnd taskEnd) {
-     int stageId = taskEnd.stageId();
-     int stageAttemptId = taskEnd.stageAttemptId();
-@@ -119,46 +75,6 @@ public synchronized void onJobStart(SparkListenerJobStart jobStart) {
-     jobIdToStageId.put(jobId, intStageIds);
-   }
-
--  @Override
--  public synchronized void onJobEnd(SparkListenerJobEnd jobEnd) {
--
--  }
--
--  @Override
--  public void onEnvironmentUpdate(SparkListenerEnvironmentUpdate environmentUpdate) {
--
--  }
--
--  @Override
--  public void onBlockManagerAdded(SparkListenerBlockManagerAdded blockManagerAdded) {
--
--  }
--
--  @Override
--  public void onBlockManagerRemoved(SparkListenerBlockManagerRemoved blockManagerRemoved) {
--
--  }
--
--  @Override
--  public void onUnpersistRDD(SparkListenerUnpersistRDD unpersistRDD) {
--
--  }
--
--  @Override
--  public void onApplicationStart(SparkListenerApplicationStart applicationStart) {
--
--  }
--
--  @Override
--  public void onApplicationEnd(SparkListenerApplicationEnd applicationEnd) {
--
--  }
--
--  @Override
--  public void onExecutorMetricsUpdate(SparkListenerExecutorMetricsUpdate executorMetricsUpdate) {
--
--  }
--
-   public synchronized  Map<String, List<TaskMetrics>> getJobMetric(int jobId) {
-     return allJobMetrics.get(jobId);
-   }
-diff --git a/spark-client/src/main/java/org/apache/hive/spark/client/RemoteDriver.java b/spark-client/src/main/java/org/apache/hive/spark/client/RemoteDriver.java
-index b77c9e8..f5b1e48 100644
---- a/spark-client/src/main/java/org/apache/hive/spark/client/RemoteDriver.java
-+++ b/spark-client/src/main/java/org/apache/hive/spark/client/RemoteDriver.java
-@@ -43,26 +43,13 @@
- import org.apache.hive.spark.client.rpc.Rpc;
- import org.apache.hive.spark.client.rpc.RpcConfiguration;
- import org.apache.hive.spark.counter.SparkCounters;
-+import org.apache.spark.JavaSparkListener;
- import org.apache.spark.SparkConf;
- import org.apache.spark.api.java.JavaFutureAction;
- import org.apache.spark.api.java.JavaSparkContext;
--import org.apache.spark.scheduler.SparkListener;
--import org.apache.spark.scheduler.SparkListenerApplicationEnd;
--import org.apache.spark.scheduler.SparkListenerApplicationStart;
--import org.apache.spark.scheduler.SparkListenerBlockManagerAdded;
--import org.apache.spark.scheduler.SparkListenerBlockManagerRemoved;
--import org.apache.spark.scheduler.SparkListenerEnvironmentUpdate;
--import org.apache.spark.scheduler.SparkListenerExecutorMetricsUpdate;
- import org.apache.spark.scheduler.SparkListenerJobEnd;
- import org.apache.spark.scheduler.SparkListenerJobStart;
--import org.apache.spark.scheduler.SparkListenerStageCompleted;
--import org.apache.spark.scheduler.SparkListenerStageSubmitted;
- import org.apache.spark.scheduler.SparkListenerTaskEnd;
--import org.apache.spark.scheduler.SparkListenerTaskGettingResult;
--import org.apache.spark.scheduler.SparkListenerTaskStart;
--import org.apache.spark.scheduler.SparkListenerUnpersistRDD;
--import org.apache.spark.scheduler.SparkListenerExecutorRemoved;
--import org.apache.spark.scheduler.SparkListenerExecutorAdded;
- import org.slf4j.Logger;
- import org.slf4j.LoggerFactory;
-
-@@ -438,21 +425,11 @@ private void monitorJob(JavaFutureAction<?> job,
-
-   }
-
--  private class ClientListener implements SparkListener {
-+  private class ClientListener extends JavaSparkListener {
-
-     private final Map<Integer, Integer> stageToJobId = Maps.newHashMap();
-
-     @Override
--    public void onExecutorRemoved(SparkListenerExecutorRemoved removed) {
--
--    }
--
--    @Override
--    public void onExecutorAdded(SparkListenerExecutorAdded added) {
--
--    }
--
--    @Override
-     public void onJobStart(SparkListenerJobStart jobStart) {
-       synchronized (stageToJobId) {
-         for (int i = 0; i < jobStart.stageIds().length(); i++) {
-@@ -500,39 +477,6 @@ public void onTaskEnd(SparkListenerTaskEnd taskEnd) {
-       }
-     }
-
--    @Override
--    public void onStageCompleted(SparkListenerStageCompleted stageCompleted) { }
--
--    @Override
--    public void onStageSubmitted(SparkListenerStageSubmitted stageSubmitted) { }
--
--    @Override
--    public void onTaskStart(SparkListenerTaskStart taskStart) { }
--
--    @Override
--    public void onTaskGettingResult(SparkListenerTaskGettingResult taskGettingResult) { }
--
--    @Override
--    public void onEnvironmentUpdate(SparkListenerEnvironmentUpdate environmentUpdate) { }
--
--    @Override
--    public void onBlockManagerAdded(SparkListenerBlockManagerAdded blockManagerAdded) { }
--
--    @Override
--    public void onBlockManagerRemoved(SparkListenerBlockManagerRemoved blockManagerRemoved) { }
--
--    @Override
--    public void onUnpersistRDD(SparkListenerUnpersistRDD unpersistRDD) { }
--
--    @Override
--    public void onApplicationStart(SparkListenerApplicationStart applicationStart) { }
--
--    @Override
--    public void onApplicationEnd(SparkListenerApplicationEnd applicationEnd) { }
--
--    @Override
--    public void onExecutorMetricsUpdate(SparkListenerExecutorMetricsUpdate executorMetricsUpdate) { }
--
-     /**
-      * Returns the client job ID for the given Spark job ID.
-      *
diff --git a/bigtop-packages/src/common/hive/patch1-HIVE-12875.diff b/bigtop-packages/src/common/hive/patch1-HIVE-12875.diff
deleted file mode 100644
index 7a6acda..0000000
--- a/bigtop-packages/src/common/hive/patch1-HIVE-12875.diff
+++ /dev/null
@@ -1,60 +0,0 @@
---- apache-hive-1.2.1-src/ql/src/java/org/apache/hadoop/hive/ql/Driver.java.orig	2015-06-18 22:51:23.000000000 +0200
-+++ apache-hive-1.2.1-src/ql/src/java/org/apache/hadoop/hive/ql/Driver.java	2016-01-27 14:34:20.179641745 +0100
-@@ -33,6 +33,7 @@
- import java.util.Queue;
- import java.util.Set;
- 
-+import com.google.common.collect.Sets;
- import org.apache.commons.lang.StringUtils;
- import org.apache.commons.logging.Log;
- import org.apache.commons.logging.LogFactory;
-@@ -557,12 +558,27 @@
-    */
-   public static void doAuthorization(BaseSemanticAnalyzer sem, String command)
-       throws HiveException, AuthorizationException {
--    HashSet<ReadEntity> inputs = sem.getInputs();
--    HashSet<WriteEntity> outputs = sem.getOutputs();
-     SessionState ss = SessionState.get();
-     HiveOperation op = ss.getHiveOperation();
-     Hive db = sem.getDb();
- 
-+    Set<ReadEntity> additionalInputs = new HashSet<ReadEntity>();
-+    for (Entity e : sem.getInputs()) {
-+      if (e.getType() == Entity.Type.PARTITION) {
-+        additionalInputs.add(new ReadEntity(e.getTable()));
-+      }
-+    }
-+
-+    Set<WriteEntity> additionalOutputs = new HashSet<WriteEntity>();
-+    for (Entity e : sem.getOutputs()) {
-+      if (e.getType() == Entity.Type.PARTITION) {
-+        additionalOutputs.add(new WriteEntity(e.getTable(), WriteEntity.WriteType.DDL_NO_LOCK));
-+      }
-+    }
-+
-+    Set<ReadEntity> inputs = Sets.union(sem.getInputs(), additionalInputs);
-+    Set<WriteEntity> outputs = Sets.union(sem.getOutputs(), additionalOutputs);
-+
-     if (ss.isAuthorizationModeV2()) {
-       // get mapping of tables to columns used
-       ColumnAccessInfo colAccessInfo = sem.getColumnAccessInfo();
-@@ -759,8 +775,8 @@
- 
-   }
- 
--  private static void doAuthorizationV2(SessionState ss, HiveOperation op, HashSet<ReadEntity> inputs,
--      HashSet<WriteEntity> outputs, String command, Map<String, List<String>> tab2cols,
-+  private static void doAuthorizationV2(SessionState ss, HiveOperation op, Set<ReadEntity> inputs,
-+      Set<WriteEntity> outputs, String command, Map<String, List<String>> tab2cols,
-       Map<String, List<String>> updateTab2Cols) throws HiveException {
- 
-     /* comment for reviewers -> updateTab2Cols needed to be separate from tab2cols because if I
-@@ -780,7 +796,7 @@
-   }
- 
-   private static List<HivePrivilegeObject> getHivePrivObjects(
--      HashSet<? extends Entity> privObjects, Map<String, List<String>> tableName2Cols) {
-+      Set<? extends Entity> privObjects, Map<String, List<String>> tableName2Cols) {
-     List<HivePrivilegeObject> hivePrivobjs = new ArrayList<HivePrivilegeObject>();
-     if(privObjects == null){
-       return hivePrivobjs;
diff --git a/bigtop-packages/src/common/tez/do-component-build b/bigtop-packages/src/common/tez/do-component-build
index 8701e5b..750772d 100644
--- a/bigtop-packages/src/common/tez/do-component-build
+++ b/bigtop-packages/src/common/tez/do-component-build
@@ -33,11 +33,17 @@ fi
 
 sed -i '/--remove-unnecessary-resolutions=false/a\\t\t<argument>--allow-root</argument>' tez-ui/pom.xml
 
+# FIXME
+sed -i -e 's#<module>tez-ui</module>#<!--<module>tez-ui</module>-->#' pom.xml
+sed -i -e 's#<module>tez-ui2</module>#<!--<module>tez-ui2</module>-->#' pom.xml
+
 BUILD_TEZ_OPTS="clean package \
--Dtar -Dhadoop.version=${HADOOP_VERSION} \
+-Dtar \
+-Dhadoop.version=${HADOOP_VERSION} \
+-Dpig.version=${PIG_VERSION} \
 -Phadoop26 \
 -DskipTests"
 
-#mvn versions:set -DnewVersion=${TEZ_VERSION}
+mvn versions:set -DnewVersion=${TEZ_VERSION}
 
 mvn ${BUILD_TEZ_OPTS} "$@"
diff --git a/bigtop-packages/src/deb/hive/hive-jdbc.install b/bigtop-packages/src/deb/hive/hive-jdbc.install
index ccd2a26..64b8e6d 100644
--- a/bigtop-packages/src/deb/hive/hive-jdbc.install
+++ b/bigtop-packages/src/deb/hive/hive-jdbc.install
@@ -1,9 +1 @@
-/usr/lib/hive/lib/commons-logging-*.jar
-/usr/lib/hive/lib/hive-exec*.jar
-/usr/lib/hive/lib/hive-jdbc*.jar
-/usr/lib/hive/lib/hive-metastore*.jar
-/usr/lib/hive/lib/hive-serde*.jar
-/usr/lib/hive/lib/hive-service*.jar
-/usr/lib/hive/lib/libfb303-*.jar
-/usr/lib/hive/lib/libthrift-*.jar
-/usr/lib/hive/lib/log4j-*.jar
+/usr/lib/hive/jdbc/hive-jdbc*.jar
diff --git a/bigtop-packages/src/deb/hive/rules b/bigtop-packages/src/deb/hive/rules
index dfb2537..6ef9b85 100755
--- a/bigtop-packages/src/deb/hive/rules
+++ b/bigtop-packages/src/deb/hive/rules
@@ -50,8 +50,9 @@ override_dh_auto_install: server2 metastore hcatalog-server webhcat-server
 	  --doc-dir=debian/tmp/usr/share/doc/${hive_pkg_name}
 	# We need to get rid of jars that happen to be shipped in other CDH packages
 	rm -f debian/tmp/usr/lib/hive/lib/hbase-*.jar debian/tmp/usr/lib/hive/lib/zookeeper-*.jar
-	ln -s /usr/lib/hbase/hbase-common.jar /usr/lib/hbase/hbase-client.jar debian/tmp/usr/lib/hive/lib
-	ln -s  /usr/lib/zookeeper/zookeeper.jar debian/tmp/usr/lib/hive/lib
+	ln -s /usr/lib/hbase/hbase-common.jar /usr/lib/hbase/hbase-client.jar /usr/lib/hbase/hbase-hadoop-compat.jar /usr/lib/hbase/hbase-hadoop2-compat.jar debian/tmp/usr/lib/hive/lib
+	ln -s /usr/lib/hbase/hbase-prefix-tree.jar /usr/lib/hbase/hbase-procedure.jar /usr/lib/hbase/hbase-protocol.jar /usr/lib/hbase/hbase-server.jar debian/tmp/usr/lib/hive/lib/
+	ln -s /usr/lib/zookeeper/zookeeper.jar debian/tmp/usr/lib/hive/lib
 	# Workaround for BIGTOP-583
 	rm -f debian/tmp/usr/lib/hive/lib/slf4j-log4j12-*.jar
 	bash debian/build-hive-install-file.sh >> debian/hive.install
diff --git a/bigtop-packages/src/rpm/hive/SPECS/hive.spec b/bigtop-packages/src/rpm/hive/SPECS/hive.spec
index 1bf63cb..bfb7107 100644
--- a/bigtop-packages/src/rpm/hive/SPECS/hive.spec
+++ b/bigtop-packages/src/rpm/hive/SPECS/hive.spec
@@ -82,7 +82,6 @@ Source15: hive-webhcat-server.svc
 Source16: hive-hcatalog-server.default
 Source17: hive-webhcat-server.default
 Source18: bigtop.bom
-#BIGTOP_PATCH_FILES
 Requires: hadoop-client, bigtop-utils >= 0.7, zookeeper, hive-jdbc = %{version}-%{release}
 Conflicts: hadoop-hive
 Obsoletes: %{name}-webinterface
@@ -262,7 +261,8 @@ cp $RPM_SOURCE_DIR/hive-site.xml .
 # We need to get rid of jars that happen to be shipped in other Bigtop packages
 %__rm -f $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/hbase-*.jar $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/zookeeper-*.jar
 %__ln_s  /usr/lib/zookeeper/zookeeper.jar  $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/
-%__ln_s  /usr/lib/hbase/hbase-common.jar /usr/lib/hbase/hbase-client.jar $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/
+%__ln_s  /usr/lib/hbase/hbase-common.jar /usr/lib/hbase/hbase-client.jar /usr/lib/hbase/hbase-hadoop-compat.jar /usr/lib/hbase/hbase-hadoop2-compat.jar $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/
+%__ln_s  /usr/lib/hbase/hbase-prefix-tree.jar /usr/lib/hbase/hbase-procedure.jar /usr/lib/hbase/hbase-protocol.jar /usr/lib/hbase/hbase-server.jar $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/
 
 # Workaround for BIGTOP-583
 %__rm -f $RPM_BUILD_ROOT/%{usr_lib_hive}/lib/slf4j-log4j12-*.jar
@@ -333,18 +333,8 @@ fi
 %doc %{doc_hive}
 %{man_dir}/man1/hive.1.*
 %exclude %dir %{usr_lib_hive}
-%exclude %dir %{usr_lib_hive}/lib
-%exclude %{usr_lib_hive}/lib/hive-jdbc-*.jar
-%exclude %{usr_lib_hive}/lib/hive-metastore-*.jar
-%exclude %{usr_lib_hive}/lib/hive-serde-*.jar
-%exclude %{usr_lib_hive}/lib/hive-exec-*.jar
-%exclude %{usr_lib_hive}/lib/libthrift-*.jar
-%exclude %{usr_lib_hive}/lib/hive-service-*.jar
-%exclude %{usr_lib_hive}/lib/libfb303-*.jar
-%exclude %{usr_lib_hive}/lib/log4j-*.jar
-%exclude %{usr_lib_hive}/lib/commons-logging-*.jar
-%exclude %{usr_lib_hive}/lib/hbase-*.jar
-%exclude %{usr_lib_hive}/lib/hive-hbase-handler*.jar
+%exclude %dir %{usr_lib_hive}/jdbc
+%exclude %{usr_lib_hive}/jdbc/hive-jdbc-*.jar
 
 %files hbase
 %defattr(-,root,root,755)
@@ -354,16 +344,8 @@ fi
 %files jdbc
 %defattr(-,root,root,755)
 %dir %{usr_lib_hive}
-%dir %{usr_lib_hive}/lib
-%{usr_lib_hive}/lib/hive-jdbc-*.jar
-%{usr_lib_hive}/lib/hive-metastore-*.jar
-%{usr_lib_hive}/lib/hive-serde-*.jar
-%{usr_lib_hive}/lib/hive-exec-*.jar
-%{usr_lib_hive}/lib/libthrift-*.jar
-%{usr_lib_hive}/lib/hive-service-*.jar
-%{usr_lib_hive}/lib/libfb303-*.jar
-%{usr_lib_hive}/lib/log4j-*.jar
-%{usr_lib_hive}/lib/commons-logging-*.jar
+%dir %{usr_lib_hive}/jdbc
+%{usr_lib_hive}/jdbc/hive-jdbc-*.jar
 
 %files hcatalog
 %defattr(-,root,root,755)
diff --git a/bigtop-packages/src/rpm/tez/SPECS/tez.spec b/bigtop-packages/src/rpm/tez/SPECS/tez.spec
index b7697c3..810facb 100644
--- a/bigtop-packages/src/rpm/tez/SPECS/tez.spec
+++ b/bigtop-packages/src/rpm/tez/SPECS/tez.spec
@@ -96,7 +96,7 @@ sh %{SOURCE2} \
 %__ln_s -f /usr/lib/hadoop/hadoop-annotations.jar $RPM_BUILD_ROOT/%{lib_tez}/hadoop-annotations.jar
 %__ln_s -f /usr/lib/hadoop/hadoop-auth.jar $RPM_BUILD_ROOT/%{lib_tez}/hadoop-auth.jar
 %__ln_s -f /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-common.jar $RPM_BUILD_ROOT/%{lib_tez}/hadoop-mapreduce-client-common.jar
-%__ln_s -f /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-core.jar $RPM_BUILD_ROOT/%{lib_tez}/hhadoop-mapreduce-client-core.jar
+%__ln_s -f /usr/lib/hadoop-mapreduce/hadoop-mapreduce-client-core.jar $RPM_BUILD_ROOT/%{lib_tez}/hadoop-mapreduce-client-core.jar
 %__ln_s -f /usr/lib/hadoop-yarn/hadoop-yarn-server-web-proxy.jar $RPM_BUILD_ROOT/%{lib_tez}/hadoop-yarn-server-web-proxy.jar
 
 %pre
diff --git a/bigtop.bom b/bigtop.bom
index 56a7661..15ad997 100644
--- a/bigtop.bom
+++ b/bigtop.bom
@@ -125,7 +125,7 @@ bigtop {
     'hadoop' {
       name    = 'hadoop'
       relNotes = 'Apache Hadoop'
-      version { base = '2.7.3'; pkg = base; release = 1 }
+      version { base = '2.7.1'; pkg = base; release = 1 }
       tarball { destination = "${name}-${version.base}.tar.gz"
                 source      = "${name}-${version.base}-src.tar.gz" }
       url     { download_path = "/$name/common/$name-${version.base}"
@@ -168,7 +168,7 @@ bigtop {
     'hive' {
       name    = 'hive'
       relNotes = 'Apache Hive'
-      version { base = '1.2.1'; pkg = base; release = 1 }
+      version { base = '2.1.1'; pkg = base; release = 1 }
       tarball { destination = "apache-${name}-${version.base}-src.tar.gz"
                 source      = destination }
       url     { download_path = "/$name/$name-${version.base}/"
@@ -178,7 +178,7 @@ bigtop {
     'tez' {
       name    = 'tez'
       relNotes = 'Apache TEZ'
-      version { base = '0.6.2'; pkg = base; release = 1 }
+      version { base = '0.8.4'; pkg = base; release = 1 }
       tarball { destination = "apache-${name}-${version.base}-src.tar.gz"
                 source      = destination }
       url     { download_path = "/$name/${version.base}/"
```

```
# ./gradlew tez-clean tez-rpm
:buildSrc:compileJava UP-TO-DATE
:buildSrc:compileGroovy UP-TO-DATE
:buildSrc:processResources UP-TO-DATE
:buildSrc:classes UP-TO-DATE
:buildSrc:jar UP-TO-DATE
:buildSrc:assemble UP-TO-DATE
:buildSrc:compileTestJava UP-TO-DATE
:buildSrc:compileTestGroovy UP-TO-DATE
:buildSrc:processTestResources UP-TO-DATE
:buildSrc:testClasses UP-TO-DATE
:buildSrc:test UP-TO-DATE
:buildSrc:check UP-TO-DATE
:buildSrc:build UP-TO-DATE
:tez_vardefines FAILED

FAILURE: Build failed with an exception.

* Where:
Script '/bigtop/packages.gradle' line: 72

* What went wrong:
Execution failed for task ':tez_vardefines'.
> sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

```