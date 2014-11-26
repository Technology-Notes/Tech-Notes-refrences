Jumbo frame? http://docs.lib.purdue.edu/cgi/viewcontent.cgi?article=2770&context=cstech

Install drest:
```
$ sudo pip install drest
```

Testing the Hadoop RM REST API:
```
>>> import drest
>>> api = drest.API('http://192.168.5.141:8088/ws/v1/')
>>> r = api.make_request('GET', '/cluster/metrics')
>>> r.data
{u'clusterMetrics': {u'totalMB': 32000, u'containersPending': 0, u'unhealthyNodes': 1, u'appsCompleted': 0, u'appsRunning': 0, u'decommissionedNodes': 0, u'lostNodes': 0, u'appsKilled': 0, u'appsPending': 0, u'availableMB': 32000, u'activeNodes': 4, u'totalNodes': 5, u'appsSubmitted': 0, u'reservedMB': 0, u'appsFailed': 0, u'rebootedNodes': 0, u'containersAllocated': 0, u'containersReserved': 0, u'allocatedMB': 0}}
```
https://github.com/datafolklabs/drest


http://www.securityweek.com/big-data-smaller-problems-configuring-kerberos-authentication-hadoop

Scrap your MapReduce! (Or, Introduction to Apache Spark), http://rahulkavale.github.io/blog/2014/11/16/scrap-your-map-reduce/

Some Commonly Used Yarn Memory Settings, http://blogs.msdn.com/b/bigdatasupport/archive/2014/11/11/some-commonly-used-yarn-memory-settings.aspx

SAS is Serial SCSI

SATA is Serial ATA

SFF (Small Form Factor) is 2.5" drives

LFF (Large FF) 3.5" drives
