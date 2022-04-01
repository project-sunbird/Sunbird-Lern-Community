# Feature/Core capabilities

### **Key Features:**

This component consists of various services which support user authentication, API management and token generation, Samza jobs for asynchronous notification along with user and organisation management.

![](<../../../.gitbook/assets/image (4).png>)

****

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
