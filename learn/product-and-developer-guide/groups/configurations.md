# Configurations

### Group Config

| Property                     | Description                                                        | Default Value |
| ---------------------------- | ------------------------------------------------------------------ | ------------- |
| max\_group\_limit            | Maximum number of groups a user can create                         | 50            |
| max\_group\_members\_limit   | Maximum number of members a group can have                         | 150           |
| max\_activity\_limit         | Maximum number of activities a group can have                      | 20            |
| enable\_userid\_redis\_cache | To enable cache for groups and group details                       | true          |
| groups\_redis\_ttl           | Group details cache duration                                       | 86400         |
| user\_redis\_ttl             | User group list cache duration                                     | 3600          |
| activityConfig               | To configure various types of activities and services to fetch it. |               |

### Cassandra Config&#x20;

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
keyspace=sunbird
```

### DB Config

```
db.ip=127.0.0.1
db.port=9042
db.username=cassandra
db.password=password
db.keyspace=sunbird
```
