# Configurations

There are various configurations that can be made via the Batch Service:

* Batch type : Open (users can enrol by themselves)&#x20;
* Batch Start date and End date and Enrolment End date
* Certificate generation for batch&#x20;
* Criteria for earning a certificate (minimum score for the course assessment)

Following are the functional configurations

| Property                                       | Description | Default Value                   |
| ---------------------------------------------- | ----------- | ------------------------------- |
| batch\_type                                    |             | 0                               |
| quartz\_course\_batch\_timer                   |             | 0 0 0/4 1/1 \* ? \*             |
| quartz\_upload\_timer                          |             | 0 0 23 1/1 \* ? \*              |
| quartz\_course\_publish\_timer                 |             | 0 0 0/1 1/1 \* ? \*             |
| quartz\_matrix\_report\_timer                  |             | 0 0 0/4 1/1 \* ? \*             |
| quartz\_shadow\_user\_migration\_timer         |             | 0 0 2 1/1 \* ? \*               |
| download\_link\_expiry\_timeout                |             | 300                             |
| quartz\_metrics\_timer                         |             | 0 0 0/4 \* \* ? \*              |
| sunbird\_user\_bulk\_upload\_size              |             | 1001                            |
| bulk\_upload\_org\_data\_size                  |             | 300                             |
| bulk\_upload\_batch\_data\_size                |             | 200                             |
| default\_date\_range                           |             | 7                               |
| sunbird\_default\_country\_code                |             | +91                             |
| quartz\_update\_user\_count\_timer             |             | 0 0 2 1/1 \* ? \*               |
| sunbird\_otp\_allowed\_attempt                 |             | 2                               |
| searchTopN                                     |             | 5                               |
| telemetry\_queue\_threshold\_value             |             | 200                             |
| file\_upload\_max\_size                        |             | 10MB                            |
| cassandra\_write\_batch\_size                  |             | 100                             |
| textbook\_toc\_max\_csv\_rows                  |             | 6500                            |
| sunbird\_texbook\_toc\_csv\_ttl                |             | 86400                           |
| sunbird\_toc\_max\_first\_level\_units         |             | 30                              |
| sunbird\_otp\_expiration                       |             | 1800                            |
| sunbird\_otp\_length                           |             | 6                               |
| sunbird\_otp\_hour\_rate\_limit                |             | 5                               |
| sunbird\_otp\_day\_rate\_limit                 |             | 20                              |
| sunbird\_rate\_limit\_enabled                  |             | true                            |
| sunbird\_sync\_read\_wait\_time                |             | 1500                            |
| sunbird\_course\_completion\_certificate\_name |             | 100PercentCompletionCertificate |
| enrollment\_list\_size                         |             | 1000                            |
