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

Following are the configuration values for different services and batch jobs:

**Sunbird Course Service:**

<details>

<summary><strong>externalResources.properties</strong></summary>

```
content_url=/content/v3/hierarchy/
ekstep_content_search_url=/v3/search
ekstep_telemetry_api_url=/data/v3/telemetry
ekstep_authorization=
ekstep_course_publish_url=/content/v3/publish
ekstep_metrics_api_url=/metrics/consumption/content-usage
ekstep_es_metrics_api_url=/metrics/creation/content-snapshot
ekstep.tag.api.url=/tag/register
ekstep.content.update.url=/system/v3/content/update/
sunbird_installation=sunbird
sunbird_analytics_api_base_url=https://dev.ekstep.in/api/data/v3
sunbird_search_service_api_base_url=https://dev.sunbirded.org/action
ekstep_api_base_url=https://dev.sunbirded.org/action
sunbird_user_org_api_base_url=https://dev.sunbirded.org/api
sunbird_search_organisation_api=/v1/org/search
sunbird_read_user_api=/private/user/v1/read
sunbird_search_user_api=/v1/user/search
sunbird_send_email_notifictaion_api=/v1/notification/email
sunbird_mail_server_host=
sunbird_mail_server_port=
sunbird_mail_server_username=
sunbird_mail_server_password=
sunbird_mail_server_from_email=support@open-sunbird.org
sunbird_username_num_digits=4
ekstep_concept_base_url=/domain/v3/{domain}/concepts/list
ekstep_domain_url=/domain/v3/list
quartz_course_batch_timer=0 0 0/4 1/1 * ? *
quartz_upload_timer=0 0 23 1/1 * ? *
quartz_course_publish_timer=0 0 0/1 1/1 * ? *
quartz_matrix_report_timer=0 0 0/4 1/1 * ? *
quartz_shadow_user_migration_timer=0 0 2 1/1 * ? *
sunbird_account_name=
sunbird_account_key=
download_link_expiry_timeout=300
sunbird_encryption_key=SunBird
sunbird_encryption_mode=local
quartz_metrics_timer =0 0 0/4 * * ? *
sunbird_encryption=ON
sunbird_allowed_login=You can use your cellphone number to login
#size of bulk upload data is 1001 including header in csv file
sunbird_user_bulk_upload_size=1001
bulk_upload_org_data_size=300
bulk_upload_batch_data_size=200
user_relations=address,education,jobProfile,orgUser
org_relations=orgUser,address
batch_relations=
default_date_range=7
sunbird_web_url=https://dev.sunbirded.org
sunbird_app_url=
sunbird_channel_read_api=/v1/channel/read
sunbird_framework_read_api=/v1/framework/read
# background actor modes {local,remote}
background_actor_provider=remote
# actor modes {local,remote}
api_actor_provider=local
# cassandra modes {standalone,embedded}
sunbird_cassandra_mode=standalone
embeddedCassandra_TimeOut=20000000000
embedded_cassandra_host=127.0.0.1
embedded_cassandra_port=9142
#file to load cassandra DB into memory.
embedded_cql_file_name=cassandra.cql
fcm.url=https://fcm.googleapis.com/fcm/send
sunbird_default_country_code=+91
#put the default evn logo url here or System Env variable with 
#same key. code will first search from EVN then here.
sunbird_env_logo_url=http://via.placeholder.com/100x50
es_search_url=http://localhost:9200
es_metrics_port=9200
system_settings_properties=phoneUnique,emailUnique
sunbird_default_welcome_sms=Welcome to DIKSHA.
quartz_update_user_count_timer=0 0 2 1/1 * ? *
sunbird_url_shortner_base_url=https://api-ssl.bitly.com/v3/shorten?access_token=
sunbird_url_shortner_access_token=
ekstep.channel.reg.api.url=/channel/v3/create
ekstep.channel.list.api.url=/channel/v3/list
quartz_channel_reg_timer=0 0 1 1/1 * ? *
sunbird_otp_allowed_attempt=2

#Telemetry producer related info
telemetry_pdata_id=local.sunbird.learning.service
telemetry_pdata_pid=learning-service
telemetry_pdata_ver=2.10.0
#elastic search top n result count for telemetry
searchTopN=5
telemetry_queue_threshold_value=200
ekstep.channel.update.api.url=/channel/v3/update

sunbird_learner_service_url=http://localhost:9000
sunbird_content_read=/content/v3/read
# Sunbird lms telemetry url
sunbird_lms_base_url=http://localhost:9000
sunbird_telemetry_api_path=/v1/telemetry
sunbird_lms_authorization=
# Sunbird Installation mail
sunbird_installation_email=dummy@dummy.org
sunbird_valid_location_types=state,district,block;cluster
# Bulk upload file max size in MB
file_upload_max_size=10
sunbird_default_channel=
# Batch size for cassandra batch operation
cassandra_write_batch_size=100
sunbird_telemetry_base_url=http://localhost:9000
sunbird_cs_search_path=/composite/v1/search
# Sunbird OpenSaber Integration
sunbird_open_saber_bridge_enable=false
sunbird_default_user_type=teacher
sunbird_installation_display_name=sunbird
sunbird_app_name="Sunbird"
sunbird_email_max_recipients_limit=100
sunbird_user_max_encryption_limit=100
sunbird_sso_client_id=
sunbird_sso_username=
sunbird_sso_password=
sunbird_sso_url=
sunbird_sso_realm=
sunbird_keycloak_user_federation_provider_id=
sunbird_keycloak_required_action_link_expiration_seconds=155520000
sunbird_url_shortner_enable=false
sunbird_user_profile_field_default_visibility=public
sunbird_api_request_lower_case_fields=source,externalId,userName,provider,loginId,email,prevUsedEmail
# Textbook TOC Api
sunbird_content_read_api=/content/v3/read
textbook_toc_allowed_content_types=TextBook,Collection,LessonPlan
sunbird_get_hierarchy_api=/content/v3/hierarchy
sunbird_update_hierarchy_api=/content/v3/hierarchy/update
textbook_toc_max_csv_rows=6500
textbook_toc_input_mapping={\"identifier\":\"Identifier\",\"frameworkCategories\":{\"board\":\"Board\",\"medium\":\"Medium\",\"gradeLevel\":\"Grade\",\"subject\":\"Subject\"},\"hierarchy\":{\"Textbook\":\"Textbook Name\",\"L:1\":\"Level 1 Textbook Unit\",\"L:2\":\"Level 2 Textbook Unit\",\"L:3\":\"Level 3 Textbook Unit\",\"L:4\":\"Level 4 Textbook Unit\"},\"metadata\":{\"description\":\"Description\",\"topic\":\"Mapped Topics\",\"keywords\":\"Keywords\",\"purpose\":\"Purpose of Content to be linked\",\"dialcodeRequired\":\"QR Code Required?\",\"dialcodes\":\"QR Code\"}}
textbook_toc_file_suppress_column_names=true
sunbird_texbook_toc_csv_ttl=86400
textbook_toc_mandatory_fields={\"Textbook\":\"Textbook Name\",\"L:1\":\"Level 1 Textbook Unit\"}
sunbird_toc_linked_content_column_name=Linked Content {0}
sunbird_toc_max_first_level_units=30
sunbird_content_cloud_storage_type=azure
sunbird_content_azure_storage_container=sunbird-content-dev
sunbird_cloud_content_folder=content
sunbird_otp_expiration=1800
sunbird_otp_length=6
sunbird_otp_hour_rate_limit=5
sunbird_otp_day_rate_limit=20
sunbird_rate_limit_enabled=true
framework_read_api_url=/framework/v3/read
sunbird_link_dial_code_api=/collection/v3/dialcode/link
sunbird_linked_content_base_url=https://dev.sunbirded.org/play/content/
textbook_toc_output_mapping={\"identifier\":\"Identifier\",\"frameworkCategories\":{\"board\":\"Board\",\"medium\":\"Medium\",\"gradeLevel\":\"Grade\",\"subject\":\"Subject\"},\"hierarchy\":{\"Textbook\":\"Textbook Name\",\"L:1\":\"Level 1 Textbook Unit\",\"L:2\":\"Level 2 Textbook Unit\",\"L:3\":\"Level 3 Textbook Unit\",\"L:4\":\"Level 4 Textbook Unit\"},\"metadata\":{\"description\":\"Description\",\"topic\":\"Mapped Topics\",\"keywords\":\"Keywords\",\"purpose\":\"Purpose of Content to be linked\",\"dialcodeRequired\":\"QR Code Required?\",\"dialcodes\":\"QR Code\"},\"linkedContent\":{\"Linked Content 1\":\"Linked Content 1\",\"Linked Content 2\":\"Linked Content 2\",\"Linked Content 3\":\"Linked Content 3\",\"Linked Content 4\":\"Linked Content 4\",\"Linked Content 5\":\"Linked Content 5\",\"Linked Content 6\":\"Linked Content 6\",\"Linked Content 7\":\"Linked Content 7\",\"Linked Content 8\":\"Linked Content 8\",\"Linked Content 9\":\"Linked Content 9\",\"Linked Content 10\":\"Linked Content 10\",\"Linked Content 11\":\"Linked Content 11\",\"Linked Content 12\":\"Linked Content 12\",\"Linked Content 13\":\"Linked Content 13\",\"Linked Content 14\":\"Linked Content 14\",\"Linked Content 15\":\"Linked Content 15\",\"Linked Content 16\":\"Linked Content 16\",\"Linked Content 17\":\"Linked Content 17\",\"Linked Content 18\":\"Linked Content 18\",\"Linked Content 19\":\"Linked Content 19\",\"Linked Content 20\":\"Linked Content 20\",\"Linked Content 21\":\"Linked Content 21\",\"Linked Content 22\":\"Linked Content 22\",\"Linked Content 23\":\"Linked Content 23\",\"Linked Content 24\":\"Linked Content 24\",\"Linked Content 25\":\"Linked Content 25\"},\"Linked Content 26\":\"Linked Content 26\",\"Linked Content 27\":\"Linked Content 27\",\"Linked Content 28\":\"Linked Content 28\",\"Linked Content 29\":\"Linked Content 29\",\"Linked Content 30\":\"Linked Content 30\"}
# For other environments
sunbird_content_search_url=/v1/content/search
# For Local
# sunbird_content_search_url=/content/v1/search
sunbird_time_zone=Asia/Kolkata
# For other environments
sunbird_dialcode_search_api=/v1/dialcode/list
# For Local
# sunbird_dialcode_search_api=/dialcode/v1/list
sunbird_cs_base_url=https://dev.sunbirded.org/api
sunbird_health_check_enable=true
sunbird_sync_read_wait_time=1500
sunbird_course_metrics_container=reports
sunbird_course_metrics_report_folder=course-progress-reports
sunbird_assessment_report_folder=assessment-reports
sunbird_gzip_size_threshold=262144
sunbird_analytics_blob_account_name=
sunbird_analytics_blob_account_key=
sunbird_redis_port=6379
sunbird_redis_host=127.0.0.1
sunbird_redis_scan_interval=2000
sunbird_cache_enable=false
sunbird_redis_connection_pool_size=250
#kafka_topics_instruction=local.coursebatch.job.request
kafka_urls=localhost:9092
sunbird_audit_event_batch_allowed=false
sunbird_fuzzy_search_threshold=0.5
sunbird_state_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212938260643843.png
sunbird_diksha_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212989820190722.png
sunbird_cert_completion_img_url=https://sunbirddev.blob.core.windows.net/orgemailtemplate/img/File-0128212919987568641.png
sunbird_reset_pass_msg=Your have requested to reset password. Click on the link to set a password: {0}
sunbird_reset_pass_mail_subject=Reset Password
sunbird_subdomain_keycloak_base_url=https://merge.dev.sunbirded.org/auth/
kafka_topics_certificate_instruction=local.issue.certificate.request
kafka_linger_ms=5
sunbird_cert_service_base_url=
sunbird_cert_download_uri=/v1/user/certs/download
#{0} instancename , {1} toaccountemail or phone in mask , {2} from account email/phone in mask
sunbird_account_merge_body=All your {0} usage details are merged into your account {1} . The account {2} has been deleted
sunbird_user_upload_error_visualization_threshold=20001
sunbird_course_completion_certificate_name=100PercentCompletionCertificate
sunbird_migrate_user_body=You can now access your {0} state teacher account using {1}. Please log out and login once again to see updated details.
#kafka_assessment_topic=local.telemetry.assess
sunbird_account_merge_subject=Account merged successfully
sunbird_pass_regex=(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[!\"#$%&'()*+,-./:;<=>?@\\[\\]^_`{|}~])(?=\\S+$).{8,}
sunbird_cert_template_url=/asset/v4/read
sunbird_user_create_sync_type=ES
sunbird_user_create_sync_topic=local.user.events
sigterm_stop_delay=40
sunbird_user_qrcode_courses_limit=5000
learning.content.props.to.add=mimeType,contentType,name,code,description,keywords,framework,copyright,topic
druid_proxy_api_host=localhost
druid_proxy_api_port=8082
druid_proxy_api_endpoint=/druid/v2/
#cert v1 template read url
sunbird_cert_template_read_url=/cert/v1/template/read
kafka_assessment_topic=
sunbird_msg_sender=
sunbird_msg_91_auth=
sunbird_api_mgr_base_url=https://dev.sunbirded.org/api
enrollment_list_size=1000
```

</details>

**Knowledge Platform Jobs:**

<details>

<summary><strong>Base Job Configurations</strong></summary>

```
kafka {
  broker-servers = "localhost:9092"
  zookeeper = "localhost:2181"
}

job {
  enable.distributed.checkpointing = false
  statebackend {
    blob {
      storage {
        account = "blob.storage.account"
        container = "kp-checkpoints"
        checkpointing.dir = "flink-jobs"
      }
    }
    base.url = "wasbs://"${job.statebackend.blob.storage.container}"@"${job.statebackend.blob.storage.account}"/"${job.statebackend.blob.storage.checkpointing.dir}
  }
}

task {
  checkpointing.compressed = true
  checkpointing.pause.between.seconds = 30000
  parallelism = 1
  checkpointing.interval = 60000
  restart-strategy.attempts = 3
  restart-strategy.delay = 30000 # in milli-seconds
}

redis {
  host = localhost
  port = 6379
  connection {
    max = 2
    idle.min = 1
    idle.max = 2
    minEvictableIdleTimeSeconds = 120
    timeBetweenEvictionRunsSeconds = 300
  }
}
lms-cassandra {
  host = "localhost"
  port = "9042"
}

neo4j {
  routePath = "bolt://localhost:7687"
  graph = "domain"
}

es {
  basePath = "localhost:9200"
}

schema {
  basePath = "https://sunbirddev.blob.core.windows.net/sunbird-content-dev/schemas/local"
  supportedVersion = {"itemset": "2.0"}
}

media_download_duration = "300 seconds"
```

</details>

<details>

<summary>Activity Aggregate Updater</summary>

```
include "base-config.conf"

kafka {
  input.topic = "sunbirddev.coursebatch.job.request"
  output.audit.topic = "sunbirddev.telemetry.raw"
  output.failed.topic = "sunbirddev.activity.agg.failed"
  output.certissue.topic = "sunbirddev.issue.certificate.request"
  groupId = "sunbirddev-activity-aggregate-updater-group"
}

task {
  window.shards = 1
  consumer.parallelism = 1
  dedup.parallelism = 1
  activity.agg.parallelism = 1
  enrolment.complete.parallelism = 1
}

lms-cassandra {
  keyspace = "sunbird_courses"
  consumption.table = "user_content_consumption"
  user_activity_agg.table = "user_activity_agg"
  user_enrolments.table = "user_enrolments"
}

redis {
  database {
    relationCache.id = 10
  }
}

dedup-redis {
  host = 11.2.4.22
  port = 6379
  database.index = 3
  database.expiry = 604800
}

threshold.batch.read.interval = 60 // In sec
threshold.batch.read.size = 1000
threshold.batch.write.size = 10

activity {
  module.aggs.enabled = true
  input.dedup.enabled = true
  filter.processed.enrolments = true
  collection.status.cache.expiry = 3600
}

service {
  search {
    basePath = "http://11.2.6.6/search"
  }
}
```

</details>

<details>

<summary>Cert Pre-Processor</summary>

```
include "base-config.conf"

kafka {
  input.topic = "sunbirddev.issue.certificate.request"
  output.topic = "sunbirddev.generate.certificate.request"
  output.failed.topic = "sunbirddev.issue.certificate.failed"
  groupId = "collection-cert-pre-processor-group"
}

task {
  consumer.parallelism = 1
  parallelism = 1
  generate_certificate.parallelism = 1
}

lms-cassandra {
  keyspace = "sunbird_courses"
  user_enrolments.table = "user_enrolments"
  course_batch.table = "course_batch"
  assessment_aggregator.table = "assessment_aggregator"
  user_activity_agg.table = "user_activity_agg"
}

cert_domain_url="https://dev.sunbirded.org"
user_read_api = "/private/user/v1/read"
content_read_api = "/content/v3/read"

service {
    content.basePath = "http://localhost:9000"
    learner.basePath = "http://localhost:9000"
}

redis-meta {
  host = localhost
  port = 6379
}
assessment.metrics.supported.contenttype = ["SelfAssess"]
enable.suppress.exception = true

```

</details>

<details>

<summary>Cert Generator</summary>

```
include "base-config.conf"

kafka {
  input.topic = "sunbirddev.generate.certificate.request"
  output.failed.topic = "sunbirddev.generate.certificate.failed"
  groupId = "certificate-generator-group"
  output.audit.topic = "sunbirddev.telemetry.raw"
}

task {
  consumer.parallelism = 1
  parallelism = 1
  notifier.parallelism = 1
  userfeed.parallelism = 1
}

service {
    certreg.basePath = "http://localhost:9000/certreg"
    learner.basePath = "http://localhost:9000/learner"
    enc.basePath = "http://localhost:9000/enc"
    rc.basePath = "http://localhost:8081/api/v1"
    rc.entity = "TrainingCertificate"
}

lms-cassandra {
  keyspace = "sunbird_courses"
  user_enrolments.table = "user_enrolments"
  course_batch.table = "course_batch"
  sbkeyspace = "sunbird"
  certreg.table ="cert_registry"
}

enable.suppress.exception = true
enable.rc.certificate = true

```

</details>

<details>

<summary>Enrolment Reconciliation</summary>

```
include "base-config.conf"

kafka {
  input.topic = "sunbirddev.batch.enrolment.sync.request"
  output.audit.topic = "sunbirddev.telemetry.raw"
  output.failed.topic = "sunbirddev.enrolment.reconciliation.failed"
  output.certissue.topic = "sunbirddev.issue.certificate.request"
  groupId = "sunbirddev-enrolment-reconciliation-group"
}

task {
  window.shards = 1
  consumer.parallelism = 1
  enrolment.reconciliation.parallelism = 1
  enrolment.complete.parallelism = 1
}

lms-cassandra {
  keyspace = "sunbird_courses"
  consumption.table = "user_content_consumption"
  user_activity_agg.table = "user_activity_agg"
  user_enrolments.table = "user_enrolments"
}

redis {
  database {
    relationCache.id = 10
  }
}

threshold.batch.write.size = 10

activity {
  module.aggs.enabled = true
  filter.processed.enrolments = true
  collection.status.cache.expiry = 3600
}

service {
  search {
    basePath = "http://11.2.6.6/search"
  }
}
```

</details>

<details>

<summary>Relation Cache Updater</summary>

```
include "base-config.conf"

kafka {
  input.topic = "sunbirddev.content.postpublish.request"
  groupId = "sunbirddev-relation-cache-updater-group"
}

task {
  consumer.parallelism = 1
  parallelism = 2
}

lms-cassandra {
  keyspace = "dev_hierarchy_store"
  table = "content_hierarchy"
}

redis {
  database.index = 10
}

dp-redis {
  host = 11.2.4.22
  port = 6379
  database.index = 5
}

```

</details>

**Sunbird Data Pipeline:**

<details>

<summary><strong>Base Job Configurations</strong></summary>

```
kafka {
  consumer.broker-servers = "localhost:9092"
  producer {
    broker-servers = "localhost:9092"
    max-request-size = 1572864
    batch.size = 98304
    linger.ms = 10
  }
}

job {
  env = "local"
  enable.distributed.checkpointing = false
  statebackend {
    blob {
      storage {
        account = "blob.storage.account"
        container = "telemetry-container"
        checkpointing.dir = "flink-jobs"
      }
    }
    base.url = "wasbs://"${job.statebackend.blob.storage.container}"@"${job.statebackend.blob.storage.account}"/"${job.statebackend.blob.storage.checkpointing.dir}
  }
}

task {
  checkpointing.compressed = true
  checkpointing.interval = 60000
  checkpointing.pause.between.seconds = 30000
  restart-strategy.attempts = 3
  restart-strategy.delay = 30000 # in milli-seconds
  parallelism = 1
  consumer.parallelism = 1
}

redisdb.connection.timeout = 30000

redis {
  host = localhost
  port = 6379
}

redis-meta {
  host = localhost
  port = 6379
}

postgres {
  host = localhost
  port = 5432
  maxConnections = 2
  user = "postgres"
  password = "postgres"
}

lms-cassandra {
  host = "localhost"
  port = "9042"
}
```

</details>

<details>

<summary>Assessment Aggregator</summary>

```
include "base-config.conf"

kafka {
  input.topic = ${job.env}".telemetry.assess"
  failed.topic= ${job.env}".telemetry.assess.failed"
  groupId = ${job.env}"-assessment-aggregator-group"
  output.certissue.topic =  ${job.env}".issue.certificate.request"
}

task {
  consumer.parallelism = 1
  downstream.parallelism = 1
  assessaggregator {
    parallelism = 1
  }
  scoreaggregator {
    parallelism = 1
  }
}

lms-cassandra {
  keyspace = "sunbird_courses"
  table = "assessment_aggregator"
  questionudttype= "question"
  enrolmentstable = "user_enrolments"
  activitytable = "user_activity_agg"
}
redis {
  database {
    relationCache.id = 10
    contentCache.id = 5
  }
}
assessment.skip.missingRecords = false
content.read.api = "http://dev.sunbirded.org/api/content/v1/read/"
user.activity.agg.type="attempt_metrics"
```

</details>
