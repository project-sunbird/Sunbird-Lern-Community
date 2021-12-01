# BATCH SERVICE

### How To Setup

This section describes how to install and run Batch Service

#### **Installation Configuration:**

User\&Org service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

* Application functional configurations and dependency service configurations has to be mentioned in externalresource.properties file

{% embed url="https://github.com/project-sunbird/sunbird-course-service/tree/release-4.5.0/course-mw/sunbird-util/sunbird-platform-core/common-util/src/main/resources" %}

* Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before batch service run to create necessary tables required. Database details need to be configured in dbconfig.propeties file.

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-cassandra-migration/cassandra-migration/src/main/resources/db/migration/cassandra" %}

*   Elastic search need to be setup with indices and mappings from [sunbird-utils](https://github.com/project-sunbird/sunbird-utils). Elastic search details need to be configured in elasticsearch.config.properties

    Pick all the indices and mappings from these folders and create index and mapping using postman.&#x20;

    PUT http://localhost:9200/\<indices\_name> Body : \<indices\_json\_content>

    PUT http://localhost:9200/\<indices\_name>/\_mapping/\_doc Body : \<mapping\_json\_content>

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-es-utils/src/main/resources" %}

#### Internal Dependencies configuration

Configure Sunbird Lern - User & Org service to fetch user information for validating the Batch creator and Mentor

#### External Dependencies configuration

Configure Sunbird Knowlg - Content service APIs  to read course metadata

Configure Sunbird Knowlg - Search service for course metadata

Configure Sunbird Inquiry to fetch QuestionSet metadata.

Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.&#x20;

### How To Use

Please refer to the Sunbird documentation link [Courses](http://docs.sunbird.org/latest/developer-docs/how-to-guide/how\_to\_create\_course\_using\_api/)

Please refer to the github readme document.

{% embed url="https://github.com/project-sunbird/sunbird-course-service/blob/release-4.5.0/README.md" %}

\<Links need to be updated with relevant information - TBD>
