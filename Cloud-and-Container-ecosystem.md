https://github.com/operator-framework/awesome-operators 
https://github.com/schoolofdevops/ultimate-kubernetes-bootcamp

https://github.com/cncf/landscape

https://dataworkssummit.com/san-jose-2018/session/containers-and-big-data/

https://www.abhishek-tiwari.com/kubernetes-for-big-data-workloads/

https://dantehranian.wordpress.com/2015/03/25/how-should-i-get-application-configuration-into-my-docker-containers/

https://lentiq.com/assets/docs/Introduction_to_Kubernetes.pdf


GUI
- kubesphere
- https://github.com/vmware/octant

https://www.sugarkube.io/


----

## k8s
- https://www.level-up.one/kubernetes-bible-beginners/
- http://kubernetesbyexample.com/
- https://github.com/eon01/kubernetes-workshop
- https://kubernetes.io/blog/2019/07/23/get-started-with-kubernetes-using-python/
- https://www.oreilly.com/ideas/kubernetes-a-simple-overview
- https://chrislovecnm.com/kubernetes/cni/choosing-a-cni-provider/

### conf validator / linter
- https://github.com/instrumenta/kubeval
- https://github.com/viglesiasce/kube-lint
----

## k8s + vagrant + ansible (for dev)
- https://www.itwonderlab.com/ansible-kubernetes-vagrant-tutorial/
- https://www.itwonderlab.com/installing-istio-in-kubernetes-under-virtualbox/
- https://github.com/ITWonderLab/ansible-vbox-vagrant-kubernetes

- https://github.com/sciabarracom/Mosaico3

- https://medium.com/@MonadicT/create-a-kubernetes-cluster-with-vagrant-and-ansible-88af7948a1fc
- https://github.com/MonadicT/kube

- https://github.com/jeremievallee/kubernetes-vagrant-ansible

----
- https://github.com/ReSearchITEng/kubeadm-playbook
- https://github.com/kairen/kubeadm-ansible

----
https://yk.surfingstudio.com/articles/automatic-setup-kubernetes-with-kubeadm-by-using-ansible-in-vagrant-environment/
```
There are already mature solutions for automatic Kubernetes setup, e.g.:

kubespray
kop
```
https://github.com/yklin/play_k8s_on_vagrant_with_ansible


https://spr.com/4-tools-to-automate-kubernetes-cluster-deployments/

https://github.com/ahmetb/kubectx

https://github.com/kubernetes-sigs/krew/

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

