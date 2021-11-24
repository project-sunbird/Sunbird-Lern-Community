# NOTIFICATION SERVICE

This micro-service helps in sending notifications to the user like SMS, email, FCM or in-app notifications. The SMS/email notifications can be send synchronously or asynchronously.

#### Key Features:

1. Sends notifications to specified users identified by phone number or email or device id/topic.
2. Can be used to send synchronous or asynchronous notifications
3. Has NO understanding of the executing workflow or action involved.
4. Only the structural integrity of the payload is verified. If invalid phone number/email is passed, the service will not validate; the end result will just be a failure.

**Adopters: **Diksha

**Contributors**: EkStep

**Last Release Date**: Mar 04 2021

**Version**: 3.7.0

#### Source Code:

[GitHub - project-sunbird/sunbird-notification-service: Microservice for sending notifications via different channels](https://github.com/project-sunbird/sunbird-notification-service)

#### API Documentation:

[http://docs.sunbird.org/latest/apis/notificationapi/](http://docs.sunbird.org/latest/apis/notificationapi/)

#### References:

[Notification service](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1057980431)

[SB-24361 : Group Notification Design](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2847178765)

[Notification Design Discussion](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2632613972)
