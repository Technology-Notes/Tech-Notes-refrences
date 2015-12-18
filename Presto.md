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