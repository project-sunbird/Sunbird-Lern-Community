# Schema

**Cassandra Database**

Below are the schema definition for different tables were given below:

```
CREATE TABLE sunbird_courses.course_batch(

)

CREATE TABLE sunbird_courses.user_enrolments (
    userid text,
    courseid text,
    batchid text,
    active boolean,
    addedby text,
    certificates list<frozen<map<text, text>>>,
    completedon timestamp,
    completionpercentage int,
    contentstatus map<text, int>,
    datetime timestamp,
    enrolleddate text,
    lastreadcontentid text,
    lastreadcontentstatus int,
    progress int,
    status int,
    PRIMARY KEY (userid, courseid, batchid)
) WITH CLUSTERING ORDER BY (courseid ASC, batchid ASC);
CREATE INDEX inx_ues_status ON sunbird_courses.user_enrolments (status);
CREATE INDEX inx_ues_certs ON sunbird_courses.user_enrolments (values(certificates));


CREATE TABLE sunbird_courses.user_content_consumption (
    userid text,
    courseid text,
    batchid text,
    contentid text,
    completedcount int,
    datetime timestamp,
    lastaccesstime text,
    lastcompletedtime text,
    lastupdatedtime text,
    progress int,
    status int,
    viewcount int,
    PRIMARY KEY (userid, courseid, batchid, contentid)
) WITH CLUSTERING ORDER BY (courseid ASC, batchid ASC, contentid ASC);
CREATE INDEX inx_ucc_status ON sunbird_courses.user_content_consumption (status);
```

**Elastic Search**&#x20;

Below are the schema definition for different tables were given below:

**course-batch index**
