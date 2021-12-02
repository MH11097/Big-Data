##### remove components 
~~~
curl -u admin:admin -H "X-Requested-By: ambari" -X DELETE \
http://ambari:8080/api/v1/clusters/analytics/services/STORM/components/NIMBUS
~~~
#####  Add new componentns not attached to host
~~~
curl -u admin:admin -H "X-Requested-By: ambari" -X POST \
http://ambari:8080/api/v1/clusters/analytics/services/STORM/components/NIMBUS
~~~
#####  attach components to new host
~~~
curl -u admin:admin -H "X-Requested-By: ambari" -X POST \ 
-d '{"host_components" : [{"HostRoles":{"component_name":"NIMBUS"}}] }' \
http://ambari:8080/api/v1/clusters/analytics/hosts?Hosts/host_name=hdp.new.host
~~~
#####  change status to installed
~~~
curl -u admin:admin -H "X-Requested-By: ambari" -i -X PUT \
-d '{"ServiceInfo": {"state" : "INSTALLED"}}' \
http://ambari:8080/api/v1/clusters/analytics/services/STORM
~~~

## States

| State |	Description |
| ------ | -----: |
| INIT |	Initial/Clean state. |
| INSTALLING |	In the process of installing. |
| INSTALL_FAILED |	Install failed. |
| INSTALLED |	State when install completed successfully. |
| STARTING |	In the process of starting. |
| STARTED |	State when start completed successfully. |
| STOPPING |	In the process of stopping. |
| UNINSTALLING |	In the process of uninstalling. |
| UNINSTALLED |	State when uninstall completed successfully. |
| WIPING_OUT |	In the process of wiping out the install. |
| UPGRADING |	In the process of upgrading the deployed bits. |
| DISABLED |	Disabled master’s backup state. |
| UNKNOWN |	State could not be determined. |

##Master Services

| Name |	Ambari Component Name |  Service | Cardinality |
| ------ | ------ | ------ |  -----: |
| NameNode |	NAMENODE |	HDFS |	1-2 |
| Secondary NameNode |	SECONDARY_NAMENODE |	HDFS |	1 |
| ResourceManger |	RESOURCEMANAGER	| YARN |	1-2 |
| Application Timeline Server |	APP_TIMELINE_SERVER |	YARN |	1 |
| HistoryServer |	HISTORYSERVER |	MAPREDUCE2	| 1 |
| Hive Metastore |	HIVE_METASTORE |	HIVE |	1-2 |
| HiveServer2 |	HIVE_SERVER |	HIVE |	1-2 |
| WebHcat Server |	WEBHCAT_SERVER |	HIVE |	1 |
| HBase Master |	HBASE_MASTER |	HBASE |	1+ |
| Spark Job History Server |	SPARK_JOBHISTORYSERVER |	SPARK |	1 |
| Nimbus Server |	NIMBUS | STORM	| 1 |
| Storm REST Server |	STORM_REST_API |	STORM |	1 |
| Storm UI |	STORM_UI_SERVER	| STORM	| 1 | |
| DRPC Server |	DRPC_SERVER	| STORM |	1 |
| Falcon Server |	FALCON_SERVER |	FALCON |	1 |
| Zookeeper |	ZOOKEEPER_SERVER	| ZOOKEEPER |	1+ (odd #) |
| Kafka Broker |	KAFKA_BROKER	| KAFKA |	1+ |
| Knox Gateway |	KNOX_GATEWAY	| KNOX	| 1+ |
| Ranger Admin Server |	RANGER_ADMIN |	RANGER |	1-3 |
| Ranger User Sync |	RANGER_USERSYNC	| RANGER |	1 |
| Ranger Key Management Server |	RANGER_KMS_SERVER |	RANGER_KMS |	1+ |
| Oozie Server |	OOZIE_SERVER |	OOZIE |	1 |
| Ganglia Server |	GANGLIA_SERVER |	GANGLIA |	1 |
| Nagios Server |	NAGIOS_SERVER |	NAGIOS |	1 |
| Ambari Metrics Service |	METRICS_COLLECTOR |	AMS |	1 |
| Zeppelin Server | ZEPPELIN_MASTER |	SPARK / HIVE |	1 |

## Slave Services
| Name |	Ambari Component Name |  Service | Cardinality |
| ------ | ------ | ------ |  -----: |
| DataNode |	DATANODE |	HDFS |	1+ |
| Journale Nodes for NameNode HA |	JOURNALNODE |	HDFS |	0+ (odd #) |
| Zookeeper Failover Service |	ZKFC |	HDFS |	0+ |
| Secondary NameNode |	NFS_GATEWAY |	HDFS |	0+ |
| Node Manager |	NODEMANAGER	 |YARN |	1+ |
| HBase RegionServer |	HBASE_REGIONSERVER |	HBASE |	1+ |
| Phoneix Query Server |	PHOENIX_QUERY_SERVER |	HBASE |	0+ |
| Storm Supervisor |	SUPERVISOR |	STORM |	1+ |
| Ganglia Metrics Collector |	GANGLIA_MONITOR |	GANGLIA |	ALL |
| Ambari Metrics Collector |	METRICS_MONITOR |	AMS |	ALL |

## Clients
| Name |	Ambari Component Name |  Service | Cardinality |
| ------ | ------ | ------ |  -----: |
| HDFS Client |	HDFS_CLIENT | 	HDFS | 	1+ |
| YARN Client |	YARN_CLIENT | 	YARN | 	1+ |
| MapReduce Client |	MAPREDUCE2_CLIENT	 | MAPREDUCE2	 | 1+ |
| Spark Client |	SPARK_CLIENT	 | SPARK | 	1+ |
| Falcon Client |	FALCON_CLIENT | 	FALCON | 	1+ |
| HBase Client |	HBASE_CLIENT | 	HBASE | 	1+ |
| Hive Client |	HIVE_CLIENT	 | HIVE	 | 1+ |
| HCat Client |	HCAT | 	HIVE | 	1+ |
| Mahout Client |	MAHOUT | 	MAHOUT | 	0+ |
| Oozie Client |	OOZIE_CLIENT | 	OOZIE | 	1+ |
| Sqoop Client |	SQOOP | 	SQOOP	 | 1+ |
| Zookeeper Client |	ZOOKEEPER_CLIENT | 	ZOOKEEPER | 	1+ |