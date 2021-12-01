# USER & ORG SERVICE

This component consists of various services which support user authentication, API management and token generation, Samza jobs for asynchronous notification along with user and organisation management.



![User Org service - Features](<../../.gitbook/assets/image (2) (1).png>)







### &#x20;<a href="#user-and-org-service" id="user-and-org-service"></a>

**Key Features:**

| Feature                        | Description                                                                                                                                                                         | API Documentation                                                                                                    |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| User Management (CRUD)         | Creation of LUA and MUA users and updating user profile, fetching user information, block and unblock user, associating user with organisation etc are implemented via this feature | http://docs.sunbird.org/latest/apis/userapi/                                                                         |
| Organisation Management (CRUD) | This feature provides CRUD APIs for maintaining organisation details.                                                                                                               | [http://docs.sunbird.org/latest/apis/orgapi/](http://docs.sunbird.org/latest/apis/orgapi/)                           |
| Location Management (CRUD)     | Provides CRUD APIs for managing location master data.                                                                                                                               | [http://docs.sunbird.org/latest/apis/locationapi/](http://docs.sunbird.org/latest/apis/locationapi/)                 |
| Consent Management             | This helps to capture user consent to share the PII in organisation level and course collection level.                                                                              | [http://docs.sunbird.org/latest/apis/consentapi/](http://docs.sunbird.org/latest/apis/consentapi/)                   |
| OTP Services                   | Helps to generate OTP and send notification either through email or phone. Also OTP validation, expiry, rate limit are managed using this feature.                                  | [http://docs.sunbird.org/latest/apis/otpapi/](http://docs.sunbird.org/latest/apis/otpapi/)                           |
| Notes Management               | User can capture notes when content is being played. This service provides the CRUD APIs for the same.                                                                              |                                                                                                                      |
| Tenant Configurations          | This service can be used to maintain tenant organisation  level configurations.                                                                                                     | [http://docs.sunbird.org/latest/apis/tenantpreferenceapi/](http://docs.sunbird.org/latest/apis/tenantpreferenceapi/) |
| Backend Services               | Admins can upload master data in to location, organisation. This service allows to create users and update user information.                                                        | [http://docs.sunbird.org/latest/apis/bulkupload/](http://docs.sunbird.org/latest/apis/bulkupload/)                   |
| <p><br>System Settings</p>     | This service is used to configure system / application settings like default organisation, various T\&C etc                                                                         | [http://docs.sunbird.org/latest/apis/systemsettingsapi/](http://docs.sunbird.org/latest/apis/systemsettingsapi/)     |

****

****

### User & Org Service: <a href="#user-and-org-service" id="user-and-org-service"></a>

This service provides a set of APIs to manage the user, organisation and location information.&#x20;

1. **Location** - It is mainly the geographical location of the organisation or user. Currently it supports - state, district, block, cluster location types.
2. **Organisation** - Supports tenant or non-tenant organisation. Tenant organisation has to have a channel and slug which is unique. Non-tenant organisations should have a channel which is having a tenant mapped to it. There should be a default organisation called ‘custodian’ created during setup.
3. **User** - User can be a LUA(Logged in User) or MUA(Managed User) user. LUA should have an email or phone number, which can be used for login. MUA will not have email and phone, their profile can be only used after logging in with LUA credentials. Each user should be mapped to custodian or other tenant orgs.&#x20;

****

****

**Source Code:**

[GitHub - project-sunbird/sunbird-lms-service: API services for Learning management system of sunbird](https://github.com/project-sunbird/sunbird-lms-service)

**Adopters:** Diksha

**Contributors**: EkStep

**Last Release Date**: Oct 21 2021

**Version :** 4.3.0&#x20;

### &#x20;<a href="#authentication" id="authentication"></a>

### &#x20;<a href="#authentication" id="authentication"></a>
