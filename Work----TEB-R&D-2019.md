Prereq:
```
# k8s node
sudo yum install -y lvm2

```

3-nodes k8s cluster (kubespray)
```
# vagrant
vagrant up
```

kubectl:
```
vagrant ssh k8s-1

sudo cp /etc/kubernetes/admin.conf .kube/config
sudo chown -R vagrant:vagrant .kube
```

helm:
```
$ curl -LO https://git.io/get_helm.sh
$ chmod 700 get_helm.sh
$ ./get_helm.sh

helm init --history-max 200
```
https://medium.com/@madeeshafernando/error-release-name-failed-namespaces-default-is-forbidden-user-99b3b6cb2720

----

Rook:
```
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/common.yaml
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/operator.yaml
kubectl -n rook-ceph get pod
```
ceph cluster:
```
# test
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/cluster-test.yaml

# production
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/cluster.yaml

kubectl get pod -n rook-ceph
```
https://github.com/rook/rook/issues/2460

ceph toolbox: https://rook.io/docs/rook/v1.1/ceph-toolbox.html
```
kubectl create -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/toolbox.yaml
kubectl -n rook-ceph get pod -l "app=rook-ceph-tools"

kubectl -n rook-ceph exec -it $(kubectl -n rook-ceph get pod -l "app=rook-ceph-tools" -o jsonpath='{.items[0].metadata.name}') bash

ceph status
ceph osd status
ceph df
rados df

```

storageClass:
```
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/csi/rbd/storageclass.yaml
kubectl get storageclass
```

PVC:
```
kubectl apply -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/csi/rbd/pvc.yaml
kubectl get pvc

# kubectl delete pvc rbd-pvc
```

test pod:
```
kubectl create -f https://raw.githubusercontent.com/rook/rook/v1.1.2/cluster/examples/kubernetes/ceph/csi/rbd/pod.yaml
kubectl describe pod csirbd-demo-pod

```

zk:
https://github.com/helm/charts/tree/master/incubator/zookeeper
```
vi values.yaml
$ helm repo add incubator http://storage.googleapis.com/kubernetes-charts-incubator
$ helm install --name zookeeper -f values.yaml incubator/zookeeper
kubectl get all -l app=zookeeper

```
```
kubectl exec zookeeper-1 -- bin/zkCli.sh create /zk_test my_data
kubectl exec zookeeper-1 -- bin/zkCli.sh set /zk_test junk
kubectl exec zookeeper-1 -- bin/zkCli.sh get /zk_test
```

----

https://tde.sktelecom.com/wiki/spaces/viewspace.action?key=TEBRDDATA

Type II, 관심분야 R&D 그룹


## 연구 내용
- 데이터 활용한 미디어 서비스 향상 방안
  - IPTV 플랫폼 진화
  - OTT / Music 서비스 강화
- 데이터 플랫폼의 진화 방향
  - 실시간 데이터 처리 시스템
  - 데이터 분석 및 활용 방안
- ML / AI 활용 방안
  - 사용자 데이터, 컨텍스트 데이터 바탕으로 인공지능 기술 활용

----

## 문제(Problem)

ywkim:
- 재사용 불가능한 코드 및 프로젝트 결과물(애플리케이션, 문서 등)
  - 노가다의 연속...
- 너무 다양하고 많은 소프트웨어 컴포넌트(프로젝트 담당자 마다 스택이 다 다름)
- (제조) 레거시 환경
  - 할말하않
- 운영 복잡도 증가
  - 클라우드 네이티브 데이터 인프라스트럭처 & 파이프라인 구축 필요


## R&D 아이템 제안(Proposals)

TBD

## 결과물(Output)

TBD

## Refs.
- A modern analytics distribution for a cloud native world, https://github.com/jayunit100/apachecon-2019-bigtop3x
- ML infra on cloud
  - Netflix, https://www.youtube.com/watch?v=FJ2lGfn9gc4
  - Lyft, https://www.youtube.com/watch?v=CbiJ_dYZXnQ
  - Netflix, https://www.slideshare.net/FaisalZakariaSiddiqi/ml-infra-for-netflix-recommendations-ai-nextcon-talk
  