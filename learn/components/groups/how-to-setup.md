# How To Setup

Please refer to the github read document.

{% embed url="https://github.com/project-sunbird/groups-service/blob/master/README.md" %}

## System Requirements

To install the group service, ensure your laptop or desktop will have following minimal system requirements:

* Operating System: Windows 7 and above, or 4.2 Mac OS X 10.0 and above/Linux
* RAM: >1.5GB
* CPU: 2 cores, >2 GHz

## Technical Specifications

| Technology   | Version | Details                                |
| ------------ | ------- | -------------------------------------- |
| Java         | 11      | group service release version >= 3.7.0 |
| Java         | 8       | group service release < 3.7.0          |
| Apache Maven | > 3.6.3 |                                        |
| Cassandra    | 3.4.4   | Used as a Database for the service     |
| Redis        | 5.0.7   | Used as Cache                          |

## Configuration

The group service excepts few configurations to run which can is available at different properties file. Further, it can be set as a system level configuration as an environment variable.

{% embed url="https://github.com/project-sunbird/groups-service/tree/master/sb-utils/src/main/resources" %}
properties files
{% endembed %}

## Internal Dependencies

### [Learner Service](how-to-setup.md#learner-service)

Learner service apis are used to **search** user details, **system settings**.

### [Sunbird Utils](how-to-setup.md#undefined)

Cassandra Migration needs to be run before group service run to create necessary table required by the group service.

### [Content Service](how-to-setup.md#undefined)

Content service APIs are being used to read the content details using READ/GET API calls.&#x20;



## External Dependencies

### [Notification service](how-to-setup.md#notification-service)

Group service used notification service to send group operations notifications to users.

### [Sunbird Telemetry](how-to-setup.md#https-telemetry.sunbird.org)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.





###

