# Schema

### ER Diagram

### User & Org **Keyspace Creation**

![](../../../.gitbook/assets/sunbird\_user\_org.png)

```
CREATE KEYSPACE IF NOT EXISTS sunbird WITH replication = {'class':'SimpleStrategy','replication_factor':1};CREATE TABLE IF NOT EXISTS  sunbird.user(id text,userId text,userName text, email text,phone text,aadhaarNo text,createdDate text,updatedDate text,updatedBy text,
```

Cassandra Migration in [sunbird-utils](https://github.com/project-sunbird/sunbird-utils) needs to be run before user\&org service run to create necessary tables required in sunbird keyspace.&#x20;

### **Table Creation in Cassandra**

```
CREATE TABLE IF NOT EXISTS  sunbird.user(id text,userId text,userName text, email text,phone text,aadhaarNo text,createdDate text,updatedDate text,updatedBy text,
lastLoginTime text,status int,firstName text,lastName text,password text,avatar text,gender text,language list<text>,subject list<text>,grade list<text>,regOrgId text,
dob text,thumbnail text,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.system_settings (id text ,field text ,value text ,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.organisation(id text, orgName text, description text,communityId text,createdBy text,createdDate text,
updatedDate text,updatedBy text,status text,parentOrgId text,orgType text,orgCode text,dateTime timestamp,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_org(id text, userId text, role text,orgId text,orgJoinDate text,orgLeftDate text,isApproved boolean,
isRejected boolean,approvedBy text,approvalDate text,updatedDate text,updatedBy text, PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_external_identity(id text, userId text, externalId text,source text,isVerified boolean,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.geo_location(id text,locationName text,rootOrgId text,type text, createdDate  text,createdBy text,updatedDate text,updatedBy text,topicName text,topicId text, PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.tenant_preference(id text,tenantName text,orgId text,role text, data text, PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_action_role(id text, actionGroupId list,roleId text, PRIMARY KEY (id));After creating keyspace and tebles in Cassandra then add the below quries in cassandra cqlsh.
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_auth(id text, userId text,createdDate text,updatedDate text,source text,PRIMARY KEY (id));// Some code
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_badge(id text, createdDate text, createdBy text, updatedDate text,updatedBy text,badgeTypeId text,receivedDate text,receiverId text,providerId text,providerName text,providerEmail text,providerPhone text,description text,validityDate int,expiryDate text,image text,isVerified boolean,isExpired boolean,isRevoked boolean,revocationReason text,revocationDate text,revokedBy text,verifiedBy text,verifiedDate text ,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_courses(id text, courseId text, courseName text, userId text, batchId text, enrolledDate text, description text,tocUrl text,status int,active boolean,delta text,grade text,progress int,lastReadContentId text, lastReadContentStatus int,addedBy text,courseLogoUrl text, dateTime timestamp, contentId text, PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_education(id text, userId text, courseName text,duration int,yearOfPassing int,percentage double,grade text,name text,boardOrUniversity text,addressId text,createdDate text,createdBy text,updatedDate text,updatedBy text, PRIMARY KEY (id));// Some code
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_external_identity(id text, userId text, externalId text,source text,isVerified boolean,PRIMARY KEY (id));
```

```
CREATE TABLE IF NOT EXISTS sunbird.user_skills(id text, userId  text, skillname text,skillnametolowercase text, addedby text, addedat text, endorsementcount int ,endorsers Map<text, text>, PRIMARY KEY (id));
```

#### Insert Values into Tables:&#x20;

**Example**:

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('custodianOrgId','custodianOrgId','0130144097756938240');
```

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('userProfileConfig','userProfileConfig','{"fields":["firstName","lastName","profileSummary","avatar","countryCode","dob","email","gender","grade","language","location","phone","subject","userName","webPages","jobProfile","address","education","skills","badgeAssertions"],"publicFields":["firstName","lastName","profileSummary"],"privateFields":["email","phone"],"csv":{"supportedColumns":{"NAME":"firstName","MOBILE PHONE":"phone","EMAIL":"email","SCHOOL ID":"orgId","USER_TYPE":"userType","ROLES":"roles","USER ID":"userId","SCHOOL EXTERNAL ID":"orgExternalId"},"outputColumns":{"userId":"USER ID","firstName":"NAME","phone":"MOBILE PHONE","email":"EMAIL","orgId":"SCHOOL ID","orgName":"SCHOOL NAME","userType":"USER_TYPE","orgExternalId":"SCHOOL EXTERNAL ID"},"outputColumnsOrder":["userId","firstName","phone","email","organisationId","orgName","userType","orgExternalId"],"mandatoryColumns":["firstName","userType","roles"]},"read":{"excludedFields":["avatar","jobProfile","address","education","webPages","skills"]},"framework":{"fields":["board","gradeLevel","medium","subject","id"],"mandatoryFields":["board","gradeLevel","medium","id"]}}');
```

```
cqlsh:sunbird> insert into sunbird.system_settings (id,field,value) values ('orgProfileConfig','orgProfileConfig','{"csv":{"supportedColumns":{"SCHOOL NAME":"orgName","BLOCK CODE":"locationCode","STATUS":"status","SCHOOL ID":"organisationId","EXTERNAL ID":"externalId","DESCRIPTION":"description"}, "outputColumns": {"organisationId":"SCHOOL ID","orgName":"SCHOOL NAME","locationCode":"BLOCK CODE","locationName":"BLOCK NAME","externalId":"EXTERNAL ID"}, "outputColumnsOrder":["organisationId","orgName","locationCode", "locationName","externalId"],"mandatoryColumns":["orgName","locationCode","status"]}}');
```
