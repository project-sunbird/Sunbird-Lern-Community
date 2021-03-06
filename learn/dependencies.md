# Dependencies

Sunbird LERN uses other Sunbird Building Blocks which are listed below:

## Sunbird Knowlg <a href="#sunbird-knowlg" id="sunbird-knowlg"></a>

Content-service in Sunbird Knowlg is used for creating, updating and validating the channel info during organisation creation. Also framework APIs in Sunbird Knowlg is used for validating the user framework selection.

{% hint style="info" %}
Resolution: Sunbird Knowlg : Content service provides capabilities such as creating content against channel and associating a framework to channel using channel configurations. Sunbird Lern - User\&Org service is user and organisation management system. It can be used independently to maintain user and organisation details and their association if some changes are made to organisation management apis to remove the content service dependency.
{% endhint %}

## Sunbird RC <a href="#sunbird-rc" id="sunbird-rc"></a>

_Credential Service_ and _Credential Registry_ in Sunbird RC is used by the batch service to generate certificates for the user.

{% hint style="info" %}
Resolution: Similar adopter service can be configured in Batch service to generate certificates instead of using Sunbird RC
{% endhint %}

## Sunbird Ed <a href="#sunbird-ed" id="sunbird-ed"></a>

Form APIs from Sunbird Ed is used to validate the profile information of the user.

{% hint style="info" %}
Resolution: User create and Update APIs in User& Org service will need to have Sunbird Ed dependency only if profileUserType and profileLocation need to be saved with user info.&#x20;
{% endhint %}

## Sunbird Telemetry <a href="#sunbird-telemetry" id="sunbird-telemetry"></a>

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.

{% hint style="info" %}
Resolution: Sunbird Lern generates various telemetry events for logging, audit, monitoring and tracing purpose. Currently the spec is tightly coupled with code base.&#x20;
{% endhint %}

## Sunbird Obsrv <a href="#sunbird-obsrv" id="sunbird-obsrv"></a>

Telemetry service and data pipeline of Sunbird Obsrv is used to process and store the telemetry events and custom data products.

{% hint style="info" %}
Resolution: Any other service which can process the telemetry events generated by Sunbird Lern can be used instead of Sunbird Obsrv.
{% endhint %}





## Sunbird inQuiry <a href="#sunbird-obsrv" id="sunbird-obsrv"></a>

&#x20;_Lern_ uses Sunbird Inquiry to fetch meta data for QuestionSets&#x20;

{% hint style="info" %}
Resolution:&#x20;
{% endhint %}



to fetch the metadata of QuestionSet.
