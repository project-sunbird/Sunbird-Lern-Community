# USER & ORG SERVICE

### Getting Started Guide

This guide helps you to install [User\&Org Service](https://github.com/project-sunbird/sunbird-lms-service) on developer machine. It includes instructions for installing the  Cassandra, Elasticsearch, Keycloak server in standalone mode, along with [admin-util ](https://github.com/project-sunbird/sunbird-apimanager-util)service for managing users and organisations.

### How To Setup

This section describes how to install and start User\&Org Service and set up the default organisation & user creation.

#### **Installation Configuration:**

User\&Org service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

* Application functional configurations and dependency service configurations has to be mentioned in externalresource.properties file

{% embed url="https://github.com/project-sunbird/sunbird-lms-service/tree/release-4.5.0/core/platform-common/src/main/resources" %}

* Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before group service run to create necessary tables required.&#x20;

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-cassandra-migration/cassandra-migration/src/main/resources/db/migration/cassandra" %}

Database details need to be configured in dbconfig.propeties file.

* Elastic search need to be setup with indices and mappings from [sunbird-utils](https://github.com/project-sunbird/sunbird-utils).

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-es-utils/src/main/resources" %}

Pick all the indices and mappings from these folders and create index and mapping using postman.&#x20;

PUT http://localhost:9200/\<indices\_name> Body : \<indices\_json\_content>

PUT http://localhost:9200/\<indices\_name>/\_mapping/\_doc Body : \<mapping\_json\_content>

After creating the indices and mappings, add respective org index to org\_alias (if using lms-service release-3.8.0 or above) and respective user index to user\_alias (if using lms-service release-3.7.0 or above)

Elastic search details need to be configured in elasticsearch.config.properties

#### External Dependencies configuration

* Configure Sunbird Knowlg - Content service APIs  to read and update channel details and to do framework validation.
* Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.
* Configure Sunbird Ed - Form APIs to validate the profile information of the user.

#### Steps to deploy and run

* Download sunbird User\&Org Service from [here](https://github.com/project-sunbird/sunbird-lms-service)
* Build : cd sunbird-lms-service  **mvn clean install**
*   Run : cd sunbird-lms-service/controller &#x20;

    &#x20;      For Debug:

    &#x20;             mvnDebug play2:run

    &#x20;      For Run:

    &#x20;             mvn play2:start
*   To check the health status of service

    Run the below curl

```
 curl --location --request GET 'http://localhost:9000/health' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json'
```

#### System  setup

*   Create custodian organisation using below API

    &#x20; [ ](http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create)[http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create](http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create)
*   After creation of custodian org, update the newly created org details as custodian org in application using below system settings APIs

    &#x20;  [http://docs.sunbird.org/latest/apis/systemsettingsapi/#operation/set](http://docs.sunbird.org/latest/apis/systemsettingsapi/#operation/set)
* Use below request body for system setting's set API

```
// to set custodian channel
{
    "request": {
        "id": "custodianOrgChannel",
        "field": "custodianOrgChannel",
        "value": "channel"// channel value from org create request
    }
}
```

```
// to set custodian org id
{
    "request": {
        "id": "custodianOrgId",
        "field": "custodianOrgId",
        "value": "id" // orgid form org create response
    }
}
```

```
// to set User Profile Config
{
    "id": "userProfileConfig",
    "field": "userProfileConfig",
    "value": "{\"fields\":[\"firstName\",\"lastName\",\"profileSummary\",\"avatar\",\"countryCode\",\"dob\",\"email\",\"gender\",\"grade\",\"language\",\"location\",\"phone\",\"subject\",\"userName\",\"webPages\",\"jobProfile\",\"address\",\"education\",\"skills\",\"badgeAssertions\"],\"publicFields\":[\"firstName\",\"lastName\",\"profileSummary\",\"userName\"],\"privateFields\":[\"email\",\"phone\"],\"csv\":{\"supportedColumns\":{\"NAME\":\"firstName\",\"MOBILE PHONE\":\"phone\",\"EMAIL\":\"email\",\"SCHOOL ID\":\"orgId\",\"USER_TYPE\":\"userType\",\"ROLES\":\"roles\",\"USER ID\":\"userId\",\"SCHOOL EXTERNAL ID\":\"orgExternalId\"},\"outputColumns\":{\"userId\":\"USER ID\",\"firstName\":\"NAME\",\"phone\":\"MOBILE PHONE\",\"email\":\"EMAIL\",\"orgId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"userType\":\"USER_TYPE\",\"orgExternalId\":\"SCHOOL EXTERNAL ID\"},\"outputColumnsOrder\":[\"userId\",\"firstName\",\"phone\",\"email\",\"organisationId\",\"orgName\",\"userType\",\"orgExternalId\"],\"mandatoryColumns\":[\"firstName\",\"userType\",\"roles\"]},\"read\":{\"excludedFields\":[\"avatar\",\"jobProfile\",\"address\",\"education\",\"webPages\",\"skills\"]},\"framework\":{\"fields\":[\"board\",\"gradeLevel\",\"medium\",\"subject\",\"id\"],\"mandatoryFields\":[\"id\"]}}"
}
```

```
// to set org profile config
{
    "id": "orgProfileConfig",
    "field": "orgProfileConfig",
    "value": "{\"csv\":{\"supportedColumns\":{\"SCHOOL NAME\":\"orgName\",\"BLOCK CODE\":\"locationCode\",\"STATUS\":\"status\",\"SCHOOL ID\":\"organisationId\",\"EXTERNAL ID\":\"externalId\",\"DESCRIPTION\":\"description\",\"ORGANISATION TYPE\":\"organisationType\"}, \"outputColumns\": {\"organisationId\":\"SCHOOL ID\",\"orgName\":\"SCHOOL NAME\",\"locationCode\":\"BLOCK CODE\",\"locationName\":\"BLOCK NAME\",\"externalId\":\"EXTERNAL ID\",\"organisationType\":\"ORGANISATION TYPE\"}, \"outputColumnsOrder\":[\"organisationId\",\"orgName\",\"locationCode\", \"locationName\",\"externalId\",\"organisationType\"],\"mandatoryColumns\":[\"orgName\",\"locationCode\",\"status\",\"organisationType\"]}}"
}
```

Once the setup done, create user using below APIs

{% embed url="http://docs.sunbird.org/latest/apis/userapi" %}
