https://github.com/cncf/landscape

https://dataworkssummit.com/san-jose-2018/session/containers-and-big-data/

https://www.abhishek-tiwari.com/kubernetes-for-big-data-workloads/

https://dantehranian.wordpress.com/2015/03/25/how-should-i-get-application-configuration-into-my-docker-containers/

----

## k8s
- https://kubernetes.io/blog/2019/07/23/get-started-with-kubernetes-using-python/
- https://www.oreilly.com/ideas/kubernetes-a-simple-overview

----



## Docker images

## Superset
- https://github.com/tylerFowler/docker-superset (https://github.com/youngwookim/docker-superset)

## Presto
- https://github.com/prestodb/docker-images
- https://github.com/Lewuathe/docker-presto-cluster (https://github.com/youngwookim/docker-presto-cluster)

## Kafka
- https://github.com/simplesteph/kafka-stack-docker-compose
- https://github.com/sknop/kafka-cluster
- https://github.com/wurstmeister/kafka-docker
- https://github.com/Landoop/schema-registry-ui/tree/master/docker

## Flink
- https://hub.docker.com/_/flink/
- https://ci.apache.org/projects/flink/flink-docs-stable/ops/deployment/docker.html

## Jupyter
- https://jupyter-docker-stacks.readthedocs.io/en/latest/
- https://www.dataquest.io/blog/docker-data-science/
```
docker run --rm --user root -p 8888:8888 -e GRANT_SUDO=yes -e JUPYTER_ENABLE_LAB=yes -v "$PWD":/work jupyter/datascience-notebook:latest

```

