```
docker run -ti --rm -v `pwd`:/bigtop bigtop/slaves:trunk-centos-6 bash -l
cd /bigtop; ./gradew pig-deb