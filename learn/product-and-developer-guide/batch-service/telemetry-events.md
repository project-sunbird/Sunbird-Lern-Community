# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org)



### List of Events <a href="#list-of-events" id="list-of-events"></a>

<details>

<summary>Audit Event</summary>

```
Sample Event:
{
   "eid":"AUDIT",
   "ets":1649241154959,
   "ver":"3.0",
   "mid":"14e5a964-402c-4291-8fb6-a9f4cd2fb6c3",
   "actor":{
      "id":"a3c92f3f-6957-4626-8196-3951f3157d05",
      "type":"User"
   },
   "context":{
      "channel":"0126796199493140480",
      "pdata":{
         "id":"staging.diksha.app",
         "pid":"lms-service",
         "ver":"1.0"
      },
      "env":"CourseBatch",
      "did":"412acce677943edd5efd7dd0e986cd2bb829862f",
      "cdata":[
         {
            "id":"do_21347643166776524811456",
            "type":"Course"
         },
         {
            "id":"01347652394590208047",
            "type":"CourseBatch"
         },
         {
            "id":"14e5a964-402c-4291-8fb6-a9f4cd2fb6c3",
            "type":"Request"
         }
      ],
      "rollup":{
         
      }
   },
   "object":{
      "id":"a3c92f3f-6957-4626-8196-3951f3157d05",
      "type":"User",
      "rollup":{
         "l1":"do_21347643166776524811456"
      }
   },
   "edata":{
      "state":"Create",
      "type":"enrol",
      "props":[
         "courseId",
         "enrolledDate",
         "userId",
         "batchId",
         "active"
      ]
   }
}
```



</details>

<details>

<summary>Error Event</summary>

```
Sample Event:
{
   "eid":"ERROR",
   "ets":1649235152368,
   "ver":"3.0",
   "mid":"49932122-143e-384a-89e8-8f6c7334856e",
   "actor":{
      "id":"0ced9624-e65b-4fd0-a0d3-2f6e86dd3ef7",
      "type":"User"
   },
   "context":{
      "channel":"01272777697873100812",
      "pdata":{
         "id":"staging.sunbird.portal",
         "pid":"lms-service",
         "ver":"1.0"
      },
      "env":"Batch",
      "did":"4bd1aa17b232e391407a2466931acf1f",
      "cdata":[
         {
            "id":"49932122-143e-384a-89e8-8f6c7334856e",
            "type":"Request"
         }
      ],
      "rollup":{
         
      }
   },
   "edata":{
      "err":"INTERNAL_ERROR",
      "stacktrace":"controllers.BaseController.createCommonExceptionResponse(BaseController.java:501)controllers.BaseCon",
      "errtype":"api_access"
   }
}
```



</details>

