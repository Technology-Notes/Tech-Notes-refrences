```
git format-patch HEAD^..HEAD --stdout > BIGTOP-1031.patch
```

```
docker run -ti --rm -v `pwd`:/bigtop bigtop/slaves:trunk-centos-7 bash -l

docker run -ti --rm -v `pwd`:/bigtop bigtop/slaves:trunk-ubuntu-16.04 bash -l

-- user namesapce
docker run -ti --rm -u jenkins -v `pwd`:/bigtop bigtop/slaves:trunk-centos-7 bash -l

CentOS 7:

yum update -y java\*
keytool -import -alias hynix -keystore  /usr/lib/jvm/java-1.8.0/jre/lib/security/cacerts -file /bigtop/sslproxy.crt

```

BOM:
```
./gradlew -Dbomfile=bigtop-metatron-dap.bom

```

http://blogs.aws.amazon.com/bigdata/post/TxNJ6YS4X6S59U/Building-and-Deploying-Custom-Applications-with-Apache-Bigtop-and-Amazon-EMR


Ansible roles and playbooks for Bigtop, https://issues.apache.org/jira/browse/BIGTOP-1584

package tests are for testing the correctness of the packages through the development cycle. They are usually pretty trivial and you can find the examples of those under bigtop-tests/test-artifacts/package/