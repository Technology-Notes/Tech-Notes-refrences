## metatron
구성, 특징, 설치 방법

### 구성
Metatron
- Metatron DAP
- Metatron PdM
- Metatron Discovery

### 배포판
- Bigtop
- CDH
- HDP

### DAP
A distribution of Hadoop and Spark based on Apache Bigtop

BOM for DAP:
- Base BOM
- Metatron BOM

### 개발
- 0. 스택 정의
- 1. 개발 및 Integration Test 
  * https://tde.sktelecom.com/stash/projects/BDD/repos/bigtop/
  * https://tde.sktelecom.com/stash/projects/BDD/repos/metatron-solution-builder
- 2. CI(Jenkins)
- 3. YUM/APT

### Deployment
절차:
- 클러스터 디자인 (토폴로지)
- 하드웨어 / 네트워크
- OS (Linux)


----

Hardware:
- TBD

Software Stack:
- Hadoop
- Spark
- Kafka
- Hive
- HBase + Phoenix

https://chris.beams.io/posts/git-commit/

homebrew versions
- https://coderwall.com/p/1ouwaq/install-specific-version-of-a-software-with-brew



http://cleverowl.uk/2015/09/30/ingesting-files-with-apache-flume/

MySQL my.cnf, https://tools.percona.com/wizard

Presto @ Twitter, http://sssslide.com/www.slideshare.net/billonahill/presto-at-twitter

Hive metastore HA, https://developer.ibm.com/hadoop/2016/04/26/bigsql-ha-configure-ha-hive-metastore-db-using-mariadb10-1/

https://discuss.zendesk.com/hc/en-us/articles/201180246-IOException-Job-status-not-available-when-mapreduce-job-exits-successfully

git diff ref - ref:
```
git diff refs/tags/0.141..0.141-t > ~/tmp/1.diff
```