# Configuration Options

| Property                     | Description                                                        | Default Value |
| ---------------------------- | ------------------------------------------------------------------ | ------------- |
| max\_group\_limit            | Maximum number of groups a user can create                         | 50            |
| max\_group\_members\_limit   | Maximum number of members a group can have                         | 150           |
| max\_activity\_limit         | Maximum number of activities a group can have                      | 20            |
| enable\_userid\_redis\_cache | To enable cache for groups and group details                       | true          |
| groups\_redis\_ttl           | Group details cache duration                                       | 86400         |
| user\_redis\_ttl             | User group list cache duration                                     | 3600          |
| activityConfig               | To configure various types of activities and services to fetch it. |               |

#### Source Code:&#x20;

[GitHub - project-sunbird/groups-service](https://github.com/project-sunbird/groups-service)
