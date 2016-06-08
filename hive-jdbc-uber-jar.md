2.0.1-DSD
```
diff --git a/pom.xml b/pom.xml
index 8fd3ee9..e85aabf 100644
--- a/pom.xml
+++ b/pom.xml
@@ -7,8 +7,7 @@
     <groupId>veil.hdp.hive</groupId>
     <artifactId>hive-jdbc-uber</artifactId>
     <packaging>jar</packaging>
-    <version>2.4.2.0-258</version>
-
+    <version>2.0.1</version>
     <name>Hive JDBC uber jar</name>
     <description>Hive JDBC uber jar</description>
 
@@ -16,8 +15,8 @@
         <maven.compiler.source>1.7</maven.compiler.source>
         <maven.compiler.target>1.7</maven.compiler.target>
         <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
-        <hive.version>1.2.1000.2.4.2.0-258</hive.version>
-        <hadoop.version>2.7.1.2.4.2.0-258</hadoop.version>
+        <hive.version>2.0.1</hive.version>
+        <hadoop.version>2.7.1</hadoop.version>
         <slf4j.version>1.7.21</slf4j.version>
     </properties>
 
@@ -156,6 +155,9 @@
                                     <include>org.slf4j:slf4j-api</include>
                                     <include>org.slf4j:log4j-over-slf4j</include>
                                     <include>org.slf4j:jcl-over-slf4j</include>
+                                    <include>org.apache.curator:curator-client</include>
+                                    <include>org.apache.curator:curator-framework</include>
+                                    <include>org.apache.zookeeper:zookeeper</include>
                                 </includes>
                             </artifactSet>
                         </configuration>
@@ -166,4 +168,4 @@
         </plugins>
     </build>
 
-</project>
\ No newline at end of file
+</project>
```