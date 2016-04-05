Linux / THP, http://blog.cloudera.com/blog/2015/01/how-to-deploy-apache-hadoop-clusters-like-a-boss/


```
# Red Hat/CentOS: /sys/kernel/mm/redhat_transparent_hugepage/defrag
# Ubuntu/Debian, OEL, SLES: /sys/kernel/mm/transparent_hugepage/defrag

if test -f /sys/kernel/mm/redhat_transparent_hugepage/enabled;then
echo never > /sys/kernel/mm/redhat_transparent_hugepage/enabled
fi
if test -f /sys/kernel/mm/redhat_transparent_hugepage/defrag;then
echo never > /sys/kernel/mm/redhat_transparent_hugepage/defrag
fi
```

CentOS6, How do I disable IPv6?:
http://wiki.centos.org/FAQ/CentOS6#head-d47139912868bcb9d754441ecb6a8a10d41781df