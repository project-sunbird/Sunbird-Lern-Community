# Configurations

### **Configuration Restriction:**&#x20;

**Max Batch Limit:** MAX\_BATCH\_LIMIT needs to be configured so that will be the max ids can be passed in a single notification object.

### Notification Config:

```
notification_category_type_config=certificateUpload,member-added
version_support_config_enable=True
feed_limit=31
```

### Cassandra Config:

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
contactPoint=127.0.0.1
port=9042
userName=cassandra
password=password
queryLoggerConstantThreshold=300
keyspace=sunbird_notifications  
```

### Cassandra Table Column Config:

```
id=id
userid=userId
createdon=createdOn
createdby=createdBy
updatedon=updatedOn
updatedby=updatedBy
templateid=templateId
expireon=expireOn
feedid=feedId
```

### Telemetry Config:

```
telemetry_pdata_id=dev.sunbird.notifications.service
telemetry_pdata_pid=notification-service
telemetry_pdata_ver=4.5.0
```
