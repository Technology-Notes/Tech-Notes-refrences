K8s(IBM), Isilon, ECS

----
Reqs -- Data lake, Data Analytics, GPU computing

Stacks:
- IBM ICP(k8s)
- Isilon for HDFS 
- Isilon for PV (?)
- EMC ECS / minio for object storage
- Presto for ad-hoc querying
- Spark / Flink for stream data computing
- Kafka / Pulsar for streaming data processing
- Beam for DI
- Nifi / Airflow for Workflow
- Serverless(like lambda or functions) for event processing -> Knative or OpenWhisk
- metrics
- logging
- minitoring
 
----
Eval
- https://github.com/IBM/deploy-ibm-cloud-private/blob/master/docs/deploy-vagrant.md
```
git clone https://github.com/IBM/deploy-ibm-cloud-private.git
cd deploy-ibm-cloud-private

# vagrant
vagrant up
vagrant destroy -f


```
----
Refs:
- https://github.com/rexray/rexray
- https://github.com/tenortim/k8s_isi_provisioner
- https://blog.min.io/the-vmware-opportunity/
- https://delltechnologiesworldonline.com/2019/connect/fileDownload/session/EFD02DFE8B09DFE51F2239001625B59F/ISG.35_Dell%20EMC%20Isilon%20Architectural%20Deep%20Dive,%20Best%20Practices,%20Tools,%20Tips%20and%20Tricks.pdf
- https://github.com/jayunit100/apachecon-2019-bigtop3x
- https://supergiant.io/blog/persistent-storage-with-persistent-volumes-in-kubernetes/
- https://lentiq.com/assets/docs/Introduction_to_Kubernetes.pdf