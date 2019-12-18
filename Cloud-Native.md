* Multi & hybrid kubernetes cluster manager
  - Kubesphere
  - https://github.com/Mirantis/kqueen
  - https://github.com/gardener/gardener
  - https://github.com/gravitational/gravity
  - https://github.com/rancher/rancher
  - ... https://ramitsurana.github.io/awesome-kubernetes/#cluster-manager

----
k8s & HCI:
- https://robin.io/blog/what-is-hyperconverged-kubernetes/
- https://www.aquasec.com/wiki/display/containers/Containers+and+Hyperconvergence

참고:
- https://diamanti.com/product/
- robin.io
- Azure stack

----
azure stack:
- https://lenovopress.com/lp1177-thinkagile-sx-for-microsoft-azure-stack-sxm4400-sxm6400-gen2
----
- https://quarkus.io/
- https://camel.apache.org/projects/camel-k/
- https://knative.dev/

----
https://github.com/lyft/flyte

----

Cloud IDE:
- https://www.eclipse.org/che/
- https://developers.redhat.com/products/codeready-workspaces/overview
  - https://www.infoq.com/news/2019/02/redhat-codeready-workspaces/
----

benchmark:
- https://github.com/leeliu/dbench

----

https://github.com/Leverege/kubernetes-book

https://github.com/shubheksha/Kubernetes-Up-and-Running-Notes

https://github.com/dennyzhang/cheatsheet-kubernetes-A4

https://github.com/dennyzhang/kubernetes-yaml-templates

Minikube + docker registry:
- https://minikube.sigs.k8s.io/docs/tasks/docker_registry/


k8s networking:
- https://medium.com/google-cloud/understanding-kubernetes-networking-pods-7117dd28727
- https://medium.com/google-cloud/understanding-kubernetes-networking-services-f0cb48e4cc82
- https://sookocheff.com/post/kubernetes/understanding-kubernetes-networking-model/
- https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0
- https://matthewpalmer.net/kubernetes-app-developer/articles/kubernetes-ingress-guide-nginx-example.html

----

https://blogs.vmware.com/cloudnative/2019/10/22/five-key-decisions-to-make-before-running-kubernetes-in-production/

https://kccnceu19.sched.com/event/MQhi/keynote-debunking-the-myth-kubernetes-storage-is-hard-saad-ali-senior-software-engineer-google

Storage: https://blog.calsoftinc.com/2019/10/demystifying-persistent-storage-myths-for-stateful-workloads-in-kubernetes.html https://calsoftinc.com/download/25085/

https://vitobotta.com/2019/08/06/kubernetes-storage-openebs-rook-longhorn-storageos-robin-portworx/

https://platform9.com/blog/kubernetes-storage-dynamic-volumes-and-the-container-storage-interface/

https://platform9.com/blog/tutorial-dynamic-provisioning-of-persistent-storage-in-kubernetes-with-minikube/

----

https://www.cloudjourney.io/articles/cloudnative/packaging-applications-for-k8s-di/

k8s + python, https://srcco.de/posts/kubernetes-and-python.html

Operator (with Helm or Ansible):
- https://coreos.com/blog/introducing-operator-framework
- https://github.com/operator-framework/getting-started
- https://blog.codecentric.de/en/2019/06/kubernetes-operators-helm/
- https://blog.openshift.com/build-kubernetes-operators-from-helm-charts-in-5-steps/
- https://blog.openshift.com/make-a-kubernetes-operator-in-15-minutes-with-helm/
- https://itnext.io/a-practical-kubernetes-operator-using-ansible-an-example-d3a9d3674d5b
- https://github.com/operator-framework/operator-sdk/blob/master/doc/user-guide.md
- https://docs.okd.io/latest/operators/osdk-getting-started.html
- https://medium.com/@cloudark/kubernetes-operator-faq-e018132c6ea2
- https://github.com/operator-framework/operator-sdk
```
# operator-sdk
$ brew install operator-sdk

# OLM
$ kubectl apply -f https://github.com/operator-framework/operator-lifecycle-manager/releases/download/0.12.0/crds.yaml
$ kubectl apply -f https://github.com/operator-framework/operator-lifecycle-manager/releases/download/0.12.0/olm.yaml

or 
$ curl -L https://github.com/operator-framework/operator-lifecycle-manager/releases/download/0.12.0/install.sh -o install.sh
$ chmod +x install.sh
$ ./install.sh 0.12.0

```
Automated provisioning in Kubernetes
- https://github.com/kubernetes-sigs/service-catalog
- https://github.com/openshift/ansible-service-broker
- https://opensource.com/article/18/2/automated-provisioning-kubernetes

----
Prometheus
- https://blog.stephane-robert.info/post/monitoring-kubernetes-k3s-prometheus-grafana/
- https://grafana.com/docs/installation/docker/#building-a-custom-grafana-image-with-pre-installed-plugins
- https://www.digitalocean.com/community/tutorials/how-to-set-up-a-prometheus-grafana-and-alertmanager-monitoring-stack-on-digitalocean-kubernetes

Minikube:
```
cd $BIGTOP_HOME

minikube start --cpus 4 --memory 4096 --container-runtime=cri-o 

kubectl cluster-info

minikube mount .:/bigtop

minikube ssh 
$ ls -als /bigtop
```

podman, buildah, cri-o
- https://developers.redhat.com/blog/2019/04/04/build-and-run-buildah-inside-a-podman-container/

https://prefetch.net/blog/2019/10/16/the-beginners-guide-to-creating-kubernetes-manifests

https://github.com/kubeapps/kubeapps

PV, PVC & StorageClass, https://www.youtube.com/watch?v=qktFhjJmFhg&feature=share

https://rancher.com/blog/2019/2019-03-21-comparing-kubernetes-cni-providers-flannel-calico-canal-and-weave/

https://www.weave.works/blog/kubernetes-faq-configure-storage-for-bare-metal-cluster

k8s storage & SAN
- https://datamattsson.tumblr.com/post/182297931146/highly-available-stateful-workloads-on-kubernetes

https://github.com/mhausenblas/stateful-kubernetes

https://github.com/openebs/node-disk-manager

https://softwareengineeringdaily.com/2019/01/11/why-is-storage-on-kubernetes-is-so-hard/

k8s web ui:
- https://srcco.de/posts/kubernetes-web-uis-in-2019.html
- K8Dash, Konstellate, Kubernetator, Kubernetes Dashboard, Kubernetes Operational View, Kubernetes Resource Report, Kubricks, Octant, Weave Scope

https://platform9.com/blog/kubernetes-helm-why-it-matters/

https://thenewstack.io/big-data-google-replaces-yarn-with-kubernetes-to-schedule-apache-spark/
- https://github.com/GoogleCloudPlatform/flink-on-k8s-operator
- https://github.com/GoogleCloudPlatform/spark-on-k8s-operator
- https://github.com/GoogleCloudPlatform/airflow-operator
- https://github.com/GoogleCloudPlatform/k8s-sqldb-operator

private registry + helm chart repo
- https://github.com/goharbor/harbor

https://www.awsgeek.com/

k8s storage:
- https://thenewstack.io/kubernetes-storage-dynamic-volumes-and-the-container-storage-interface
- https://thenewstack.io/tutorial-dynamic-provisioning-of-persistent-storage-in-kubernetes-with-minikube/
- https://cloud.ibm.com/docs/containers?topic=containers-kube_concepts

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

https://github.com/kubernetes/examples

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

