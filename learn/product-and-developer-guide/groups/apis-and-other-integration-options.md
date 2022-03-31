# APIs and Other Integration Options

### **API**&#x20;

&#x20;**** [Group Management APIs](http://docs.sunbird.org/latest/apis/groupapi/)

&#x20;CRUDS APIs need to be developed\
&#x20;All read, update, delete will require the group identifier.\
&#x20;Search can take up members.

&#x20;Sample Read Group API response with members and activities

```
{
    "id": "api.group.read",
    "ver": "v1",
    "ts": "2020-07-14 16:40:55:077+0000",
    "params": null,
    "result": {
        "membershipType": "invite_only",
        "updatedBy": "33141e91-bf0e-4242-83db-ec3c6ff34367",
        "createdBy": "33141e91-bf0e-4242-83db-ec3c6ff34367",
        "activities": [],
        "members": [
            {
                "userId": "33141e91-bf0e-4242-83db-ec3c6ff34367",
                "groupId": "b4d28662-7a0d-447d-9620-cd880c37df4c",
                "role": "admin",
                "status": "active",
                "createdOn": "2020-07-14 12:18:05:650+0000",
                "createdBy": "33141e91-bf0e-4242-83db-ec3c6ff34367",
                "updatedOn": null,
                "updatedBy": null,
                "removedOn": null,
                "removedBy": null,
                "name": "Name of User"
            }
        ],
        "activities": [
            {
                "id": "do_2130654356933754881407",
                "type": "Course",
                "activityInfo": {
                    "subject": [
                        "Science"
                    ],
                    "channel": "0124784842112040965",
                    "downloadUrl": "https://ntpstagingall.blob.core.windows.net/ntp-content-staging/ecar_files/do_2130654356933754881407/report-course_1594902148469_do_2130654356933754881407_1.0_spine.ecar",
                    "organisation": [
                        "Odisha"
                    ],
                    "language": [
                        "English"
                    ],
                    "mimeType": "application/vnd.ekstep.content-collection",
                    "variants": {
                        "online": {
                            "ecarUrl": "https://ntpstagingall.blob.core.windows.net/ntp-content-staging/ecar_files/do_2130654356933754881407/report-course_1594902148617_do_2130654356933754881407_1.0_online.ecar",
                            "size": 10020.0
                        },
                        "spine": {
                            "ecarUrl": "https://ntpstagingall.blob.core.windows.net/ntp-content-staging/ecar_files/do_2130654356933754881407/report-course_1594902148469_do_2130654356933754881407_1.0_spine.ecar",
                            "size": 168870.0
                        }
                    },
                    "medium": [
                        "Hindi"
                    ],
                    "leafNodes": [
                        "do_2130640217720832001141",
                        "do_21303481786022297611129",
                        "do_2130652418787000321420",
                        "do_213063267561111552186"
                    ],
                    "objectType": "Content",
                    "batches": [
                        {
                            "createdFor": [
                                "0124784842112040965"
                            ],
                            "endDate": "2020-08-09",
                            "name": "Test group",
                            "batchId": "0130654458430996488",
                            "enrollmentType": "open",
                            "enrollmentEndDate": "2020-08-01",
                            "startDate": "2020-07-16",
                            "status": 1
                        }
                    ],
                    "gradeLevel": [
                        "Class 9"
                    ],
                    "appIcon": "https://ntpstagingall.blob.core.windows.net/ntp-content-staging/content/do_2130654356933754881407/artifact/1920_1080_1569831930335.thumb.jpeg",
                    "lastUpdatedOn": "2020-07-16T12:22:28.047+0000",
                    "contentType": "Course",
                    "identifier": "do_2130654356933754881407",
                    "pkgVersion": 1.0,
                    "framework": "rj_k-12_2",
                    "size": 168870.0,
                    "createdBy": "ca828836-ebec-4c7a-a6e7-393692ac0549",
                    "leafNodesCount": 4,
                    "name": "Report course",
                    "board": "State (Rajasthan)",
                    "status": "Live",
                    "resourceType": "Course"
                }
            }
        ],
        "name": "TestGroup1",
        "description": "Test group description1",
        "updatedOn": "2020-07-14 12:19:22:998+0000",
        "id": "b4d28662-7a0d-447d-9620-cd880c37df4c",
        "createdOn": "2020-07-14 12:18:05:642+0000",
        "status": "active"
    },
    "responseCode": 200
}
```

#### Suspend and Delete Group <a href="#suspend-and-delete-group" id="suspend-and-delete-group"></a>

The group can be suspended by the admin which makes the groups in the suspended state where the only operation is allowed is to be reactivated by the admin. All other operations such as adding the member, adding an activity, or any type of update are disallowed.

The group can be suspended, reactivate, and can be deleted through an update group API call.T

#### Suspend the Group

```
curl --location --request PATCH 'http://localhost:9000/v1/group/update' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
   "request":{
         "groupId": "5a53683e-c012-422a-85b6-f0e170aca412",
         "status":"suspended"
   }
    
}'
```

```
{
   "request":{
        "groupId":"5a53683e-c012-422a-85b6-f0e170aca412",
        "status":"suspended"
   }
    
}
```

#### Reactivate Group

```
curl --location --request PATCH 'http://localhost:9000/v1/group/update' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
   "request":{
         "groupId": "5a53683e-c012-422a-85b6-f0e170aca412",
         "status":"active"
   }
    
}'
```

```
{
   "request":{
        "groupId":"5a53683e-c012-422a-85b6-f0e170aca412",
        "status":"active"
   }
    
}
```

#### Delete Group

```
curl --location --request POST 'http://localhost:9000/v1/group/delete' \
--header 'Accept: application/json' \
--header 'Content-Type: application/json' \
--data-raw '{
   "request":{
         "groupId": "ebd793f7-4c75-4fa4-9ec1-9608d1c72ac2"
      
   }
    
}'
```

