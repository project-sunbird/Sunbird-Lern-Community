# GROUPS

Groups is a pluggable tool on Sunbird that enables users to create virtual groups of users, assign assets to the Group, as well as review asset progress of the users.

#### Key Features:

1. Group Creation - Any type of user could create groups and any number of groups can be created. Maximum 50 groups can be created by a user as per the default configuration.
2. Add/remove members - Members can be either user or managed user. Default configuration for maximum number of members is 150.
3. Groups can be associated with activities - Activity is a specific interest associated with the group. Example: Content, Discussion, Announcement. Upto 20 activities can be added in a group as per the default configuration.
4. Activities that can be added to the group are configured using activityConfig.json. This configuration enables to connect to various services to fetch activities.
5. Group related in-app notifications are enabled with the help of Sunbird Lern - Notification service.
6. Redis cache support can be enabled for caching groups list and the group details using configuration. For a user group list, the default caching time is 3600 seconds and that of each group details is 86400 seconds.

Groups component comprises of the Groups Service (APIs) as well as the Groups UX tools. Groups UX is still part of Sunbrid-Ed.



**Adopters: **Diksha

**Contributors**: EkStep

**Last Release Date**: Sep 17 2021

**Version**: **release-4.2.0**

#### Source Code:

[GitHub - project-sunbird/groups-service](https://github.com/project-sunbird/groups-service)

#### API Documentation:

[Group Management APIs](http://docs.sunbird.org/latest/apis/groupapi/)

#### Dependencies:

{% tabs %}
{% tab title="Sunbird Lern - Notification Service" %}
Group Service uses Notification Service to sent out in-app notifications
{% endtab %}

{% tab title="Sunbird Lern - UserOrg Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.
{% endtab %}

{% tab title="Sunbird Knowledge -Content Service" %}
There is a dependency with Content Service to fetch the activities that need to be added to the group. Activity types are configurable in activityConfig.json. Other services can be plugged in here to fetch activities from different sources...
{% endtab %}
{% endtabs %}

#### References:

[User and Groups in Schooling@Home](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1416200208/User+and+Groups+in+Schooling+Home)

[\[Design\] Groups as NPM module](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2956099585)
