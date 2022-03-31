# Installation Guide

### How To Setup

This section describes how to install and run Batch Service

#### **Installation Configuration:**

Batch service requires few configurations to be set in properties file. Some of these properties can also be set as environment variables.

* Application functional configurations and dependency service configurations has to be mentioned in externalresource.properties file

{% embed url="https://github.com/project-sunbird/sunbird-course-service/tree/release-4.5.0/course-mw/sunbird-util/sunbird-platform-core/common-util/src/main/resources" %}

* Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before batch service run to create necessary tables required. Database details need to be configured in dbconfig.propeties file.

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-cassandra-migration/cassandra-migration/src/main/resources/db/migration/cassandra" %}

*   Elastic search need to be setup with indices and mappings from [sunbird-utils](https://github.com/project-sunbird/sunbird-utils). Elastic search details need to be configured in elasticsearch.config.properties

    Pick all the indices and mappings from these folders and create index and mapping using postman.&#x20;

    PUT http://localhost:9200/\<indices\_name> Body : \<indices\_json\_content>

    PUT http://localhost:9200/\<indices\_name>/\_mapping/\_doc Body : \<mapping\_json\_content>

{% embed url="https://github.com/project-sunbird/sunbird-utils/tree/master/sunbird-es-utils/src/main/resources" %}

**Installation :**&#x20;

* [ ] Fork https://github.com/project-sunbird/sunbird-course-service and clone the latest release branch&#x20;
* [ ] Download all the files at https://drive.google.com/drive/folders/1VSu3wa70E7zbwtBw-dUAKa7qgL\_yrMUW?usp=sharing
* [ ] Export all in lms-config.sh&#x20;
* [ ] Create cassandra keyspace and tables using courses\_db.cql&#x20;
* [ ] Create ES index using course-batch.json and course-batch-mapping.json&#x20;
* [ ] Build course-service with maven clean install -DskipTests
* [ ] cd service&#x20;
* [ ] To run the service, maven play2:run&#x20;
* [ ] To Debug the service, mvnDebug play2:run

**How to run Flink?**&#x20;

* Install Flink-1.12.2 Build respective flink job.&#x20;
* Start docker Start kafka.&#x20;
* Start databases used by the job like cassandra, redis, ES&#x20;
* Create the input and output topics of flink job&#x20;
* Export KUBECONFIG=\~/.kube/flink-kp-dev.yml kubectl config set-context --current --namespace=flink-kp-dev kubectl config view --minify | grep namespace:&#x20;
* cd flink-1.12.2&#x20;
* ./bin/start-cluster.sh&#x20;
* Check if flink cluster is started or not by http://localhost:8081/#/overview&#x20;
* Submit the job. Below is a sample request bin/flink run -m localhost:8081 knowledge-platform-jobs/enrolment-reconciliation/target/enrolment-reconciliation-1.0.0.jar&#x20;
* Push events and see if it is being consumed by the job.&#x20;
* Ctrl+C will job the flink.&#x20;
* Stop the flink cluster with bin/stop-cluster.sh

Internal Dependencies configuration

Configure Sunbird Lern - User & Org service to fetch user information for validating the Batch creator and Mentor

#### External Dependencies configuration

Configure Sunbird Knowlg - Content service APIs  to read course metadata

Configure Sunbird Knowlg - Search service for course metadata

Configure Sunbird Inquiry to fetch QuestionSet metadata.

Configure Kafka setup for sending telemetry events. Sunbird Telemetry is a specification to instrument all the key events.&#x20;
