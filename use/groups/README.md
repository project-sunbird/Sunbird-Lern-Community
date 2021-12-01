# GROUPS

### How To Setup

Please refer to the github readme document.

{% embed url="https://github.com/project-sunbird/groups-service/blob/master/README.md" %}

### **Installation Configuration:**

The group service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/project-sunbird/groups-service/tree/master/sb-utils/src/main/resources" %}

Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before group service run to create necessary table required by the group service.&#x20;

Database details need to be configured in dbconfig.propeties file.

Redis cache configurations has to be mentioned in externalresource.properties file

#### Internal Dependencies configuration

Configure Sunbird Lern - User & Org service to search user details, system settings

Configure Sunbird Lern - Notification service to send group operations notifications to users.

#### External Dependencies configuration

Configure Sunbird Knowlg - Content service APIs  to read the content details using READ/GET API calls

Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.&#x20;

