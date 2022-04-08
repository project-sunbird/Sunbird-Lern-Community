# Dependencies

### Dependency Services:

{% tabs %}
{% tab title="Sunbird Lern - Notification Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.
{% endtab %}

{% tab title="Sunbird Lern - UserOrg Service" %}
Group Service connects to UserOrg Service to fetch user/member information. Any other service which has user information in a similar schema can be plugged in instead of this dependency.
{% endtab %}

{% tab title="Sunbird Knowledge -Content Service" %}
There is a dependency with Content Service to fetch the activities that need to be added to the group. Activity types are configurable in activityConfig.json. Other services can be plugged in here to fetch activities from different sources...
{% endtab %}
{% endtabs %}

### Configurations:&#x20;

#### Group Service:&#x20;

```
groups_redis_ttl=864004
user_redis_ttl=3600
max_group_members_limit =150
max_activity_limit=20
max_group_limit=50
```



#### Notification Service:

```
notification_service_base_url=
notification_service_api_url=/v2/notification/send
enable_tenant_config=custchannel,tc
sunbird_us_system_setting_url=/api/data/v1/system/settings/list
sunbird_us_org_read_url=/v1/org/read
```



#### UserOrg Service:&#x20;

```
LEARNER_SERVICE_PORT=
sunbird_user_service_search_url=/private/api/user/v1/search
sso.url=
sso.realm=sunbird
sso.connection.pool.size=20
sso.enabled=true
```

#### Content Service:

```
CONTENT_SERVICE_PORT=
sunbird_cs_search_url=
```



#### References:&#x20;

[User and Groups in Schooling@Home](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/1416200208/User+and+Groups+in+Schooling+Home)

[\[Design\] Groups as NPM module](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/2956099585)
