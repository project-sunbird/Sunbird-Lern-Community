# Trying out Sunbird Lern

### Getting Started Guide

This guide helps you to install [lern](https://github.com/project-sunbird/sunbird-lms-service) on developer machine. It includes instructions for installing the  Cassandra, Elasticsearch, Keycloak server in standalone mode, along with [admin-util ](https://github.com/project-sunbird/sunbird-apimanager-util)service for managing users and organizations.

### System Requirements <a href="#system-requirements" id="system-requirements"></a>

To install Sunbird Lern, ensure that your laptop or desktop has the following minimum system requirements:

* Operating System: Windows 7 and above, or 4.2 Mac OS X 10.0 and above/Linux
* RAM: >4 GB
* CPU: 4 cores, >2 GHz

### Technical Specification <a href="#installing-a-sample-instance-of-keycloak" id="installing-a-sample-instance-of-keycloak"></a>

| Technology    | Version |
| ------------- | ------- |
| JAVA          | 11      |
| Keycloak      | 7.0.1   |
| Elasticsearch | 6.3.0   |
| Cassandra     | 3.11.6  |

### Running Sunbird Lern <a href="#installing-a-sample-instance-of-keycloak" id="installing-a-sample-instance-of-keycloak"></a>

This section describes how to install and start lern service and set up the initial organization & user.

#### Steps

* Download sunbird lern from [here](https://github.com/project-sunbird/sunbird-lms-service)
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

### System setting Setup

*   Create custodian organization using below api

    &#x20; [ ](http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create)[http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create](http://docs.sunbird.org/latest/apis/orgapi/#operation/Organisation%20Create)
*   After successful creation of custodian org, update system setting using below apis

    &#x20;  [http://docs.sunbird.org/latest/apis/systemsettingsapi/#operation/set](http://docs.sunbird.org/latest/apis/systemsettingsapi/#operation/set)
* Use below request body for system setting using set api

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

Once the system setting setup done, you can create user using below apis

&#x20; [http://docs.sunbird.org/latest/apis/userapi/](http://docs.sunbird.org/latest/apis/userapi/)

##

####

\
