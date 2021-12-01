# NOTIFICATION SERVICE

**Repository for sunbird notification service**:&#x20;

GitHub - [https://github.com/project-sunbird/sunbird-notification-service ](https://github.com/project-sunbird/sunbird-notification-service)



**Deployment steps:**&#x20;

service-seed-without-router Play, Akka seed project without router implementation.

Use this for creating a play-based service that leverages all internal actors. By default, runs http on port 9000.

Note 1.In this Application , throw only org.sunbird.BaseException

Build&#x20;

&#x20;   Execute clean install mvn clean install&#x20;

Run&#x20;

&#x20;  For debug mode, cd notification-service/service&#x20;

&#x20;   mvn play2:dist&#x20;

&#x20;    mvn play2:run

&#x20;  For run mode, cd notification-service/service&#x20;

&#x20;    mvn play2:dist&#x20;

&#x20;    mvn play2:start

Verify running status - Hit the following Health check curl command

&#x20;   curl -X GET \ http://localhost:9000/health \ -H 'Postman-Token: 6a5e0eb0-910a-42d1-9077-         c46f6f85397d' \ -H 'cache-control: no-cache'

And, a successful response must be like this:

{"id":"api.200ok","ver":"v1","ts":"2019-01-17 16:53:26:286+0530","params":{"resmsgid":null,"msgid":"8e27cbf5-e299-43b0-bca7-8347f7ejk5abcf","err":null,"status":"success","errmsg":null},"responseCode":"OK","result":{"response":{"response":"SUCCESS","errors":\[]}}}

**Dependencies:**

There is no dependency when sending notifications in sync mode. But while sending async notifications, application needs notification samza job to run.

Repository for sunbird jobs: [https://github.com/project-sunbird/sunbird-lms-jobs ](https://github.com/project-sunbird/sunbird-lms-jobs)

**Steps for running notification samza job:**

The following wiki page contains steps to run notification samza job.

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1087307787/How+to+Set+up+kafka+hadoop+samza+in+local" %}
notification-job
{% endembed %}

