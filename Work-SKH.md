K8s(IBM), Isilon, ECS

----
Reqs -- Data lake, Data Analytics, GPU computing

Stacks:
- IBM k8s
- Isilon for PV
- ECS/minio for object storage
- Presto for ad-hoc querying
- Spark for computing
- Kafka / Pulsar for Messaging
- Beam for DI

Refs:
- https://github.com/rexray/rexray
- https://github.com/xphyr/k8s_isi_provisioner