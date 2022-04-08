# Configurations

### Elastic Search Config:

```
es.cluster.name=test
es.host.name=localhost
es.host.port=9300
```

```
es.cluster.name=test
es.host.name=localhost
es.host.port=9300
```

### Notification Config:

### Notification Config:

```
sunbird.msg.91.country=91
sunbird.msg.91.sender=TesSun
sunbird.msg.91.auth=
sunbird.msg.91.method=POST
sunbird.msg.91.route=4
sunbird.msg.91.baseurl=http://api.msg91.com/
sunbird.msg.91.get.url=api/sendhttp.php?
sunbird.msg.91.post.url=api/v2/sendsms
#NIC
nic_sms_gateway_provider_base_url=https://smsgw.sms.gov.in/failsafe/HttpLink
```

```
sunbird.msg.91.country=91
sunbird.msg.91.sender=TesSun
sunbird.msg.91.auth=
sunbird.msg.91.method=POST
sunbird.msg.91.route=4
sunbird.msg.91.baseurl=http://api.msg91.com/
sunbird.msg.91.get.url=api/sendhttp.php?
sunbird.msg.91.post.url=api/v2/sendsms
#NIC
nic_sms_gateway_provider_base_url=https://smsgw.sms.gov.in/failsafe/HttpLink
```

### Mail Template Config

### Mail Template Config

```
orgName=Diksha
onboarding_mail_subject=Welcome to {0}
onboarding_welcome_message=Welcome to {0}
onboarding_welcome_mail_body=Please ensure that you change your password according to instructions when you log in for the first time.
mail_note=Note: This is an automatic alert email. Replies to this mail box will not be monitored. If you are not the intended recipient of this message, or need to communicate with the team, write to
```

```
orgName=Diksha
onboarding_mail_subject=Welcome to {0}
onboarding_welcome_message=Welcome to {0}
onboarding_welcome_mail_body=Please ensure that you change your password according to instructions when you log in for the first time.
mail_note=Note: This is an automatic alert email. Replies to this mail box will not be monitored. If you are not the intended recipient of this message, or need to communicate with the team, write to
```

### sso Config:

### sso Config:

```
sso.url=
sso.realm=sunbird
sso.connection.pool.size=20
sso.enabled=true
```

```
sso.url=
sso.realm=sunbird
sso.connection.pool.size=20
sso.enabled=true
```

### Cassandra Config:

### Cassandra Config:

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
queryLoggerConstantThreshold=300
```

```
coreConnectionsPerHostForLocal=4
coreConnectionsPerHostForRemote=2
maxConnectionsPerHostForLocal=10
maxConnectionsPerHostForRemote=4
maxRequestsPerConnection=32768
heartbeatIntervalSeconds=60
poolTimeoutMillis=0
queryLoggerConstantThreshold=300
```

