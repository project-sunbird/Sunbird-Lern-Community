# GROUPS

### How To Setup

Please refer to the github readme document.

{% embed url="https://github.com/project-sunbird/groups-service/blob/master/README.md" %}

### Configuration

The group service excepts few configurations to run which can is available at different properties file. Further, it can be set as a system level configuration as an environment variable.

{% embed url="https://github.com/project-sunbird/groups-service/tree/master/sb-utils/src/main/resources" %}

Cassandra Migration in sunbird-utils needs to be run before group service run to create necessary table required by the group service.&#x20;

Database details need to be configured in dbconfig.propeties file.

Redis cache configurations has to be mentioned in externalresource.properties file

#### Internal Dependencies configuration

Configure **User & Org service -** User & Org sevice apis are used to search user details, system settings

Configure Content service APIs  to read the content details using READ/GET API calls

#### External Dependencies configuration

Configure Group service to send group operations notifications to users.

Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.&#x20;

