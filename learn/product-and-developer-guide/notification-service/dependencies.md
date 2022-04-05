# Dependencies

The Notification service requires a few configurations to be set in the properties file. Some of these properties can also be set as environment variables.

{% embed url="https://github.com/project-sunbird/sunbird-notification-service/tree/release-4.5.0/sb-utils/src/main/resources" %}

{% embed url="https://github.com/project-sunbird/sunbird-notification-service/tree/master/notification-sdk/src/main/resources" %}

### **Configuration**:

```
sunbird_notification_default_country_code=91
sunbird_notification_msg_default_sender=TesSun
sunbird_msg_91_auth=
sunbird_msg_91_route=4
sunbird_msg_91_baseurl=http://api.msg91.com/
sunbird_msg_91_get_url=api/sendhttp.php?
sunbird_msg_91_post_url=api/v2/sendsms
sunbird_fcm_url=https://fcm.googleapis.com/fcm/send
sunbird_notification_otp_length=4
sunbird_notification_otp_default_message=Your verification code is ##OTP##
sunbird_notification_otp_expiry_in_minute=30
sunbird_mail_server_from_email=support@open-sunbird.org
sunbird_mail_server_host=
sunbird_mail_server_password=
sunbird_mail_server_username=
sunbird_mail_server_port=
sunbird_us_system_setting_url=/api/data/v1/system/settings/list
sunbird_us_org_read_url=/v1/org/read
LEARNER_SERVICE_PORT=
sunbird_sso_client_id=
sunbird_sso_username=
sunbird_sso_password=
sunbird_sso_url=
sunbird_sso_realm=
```



