# APIs and Other Integration Options

#### API Documentation:

[http://docs.sunbird.org/latest/apis/notificationapi/](http://docs.sunbird.org/latest/apis/notificationapi/)

Detailed API information present in this Reference -  [API Document](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2847178765/SB-24361+Group+Notification+Design)

**Example**:

Group Notification will use the new notification create API to create notifications as defined in the document [Notification Design Discussion](https://project-sunbird.atlassian.net/wiki/spaces/UM/pages/2632613972/SB-24321+Group+Notification+Design+Discussion).

#### Notification Create :  <a href="#notification-create" id="notification-create"></a>

The new notification create API will be used to create a new notifications for the members:

```
curl --location --request POST 'https://dev.sunbirded.org/api/user/notification/create' \
--header 'Content-Type: text/plain' \
--data-raw '{
  "request": {
   "notificatios":[
    { 
    "ids": ["37634e84-70db-421e-898e-06e6554c4483"],    //userId
    "priority":1,                                        
    "type":"FEED",     
    "action": {                                         
          "type": "add-member",                        
          "category": "group-feed",                    
          "template":{
              "type":"JSON",                      //HTML, STRING, XML or JSON
              "params":{
                  "param1":"Math's Activity",
                  "param2": "Test"
                }
           }
          "createdBy":{
		"id":"f10d5216-6b96-404c-8d1c-cc1f720d910d",
		"name":"John",
		"type": "User"				 //User or System
	    },    
          "additionalInfo":{
                "group":{
                    "id":"123434"
                     "name":"Test"
	   	 },
		"groupRole":"admin",                     // Role of the users in the Ids field.
	  	"activity":{
                     "id":"do_12443",
                     "type": "Course",
                     "name":"Math's Activity"  
	    	}		     
           }
     }
   }
   }
   ]
}'
```

#### Notification Read :  <a href="#notification-read" id="notification-read"></a>

The Notification read API will be used by the client to read the notifications.

```
 {
    "id": "api.notification.feed.read.e79ee6a4-d79c-4236-9e05-f754010932d6",
    "ver": "v1",
    "ts": "2021-05-10 05:54:35:649+0000",
    "params": {
        "resmsgid": null,
        "msgid": "8470ecb7fa05d7d22313a30c9a16927d",
        "err": null,
        "status": "success",
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "response": {
            "userFeed": [
                {
                    "id": "ddab7b78-5978-4a11-b7f8-6594c7a6e7b8",
                    "userId": "e79ee6a4-d79c-4236-9e05-f754010932d6",                    
                    "priority": 1,
                    "createdBy": "e79ee6a4-d79c-4236-9e05-f754010932d6",
                    "status": "unread",                                        
                    "action": {
                            "type": "add-member",
                            "category": "groups",
                            "template": {
                              "data": "{"title": "आपको Test group में जोड़ दिया गया है"}",
                              "type": "JSON",
                               "ver":  "4.2.0"
                            }, 
                            "createdBy":{
				    "id":"e79ee6a4-d79c-4236-9e05-f754010932d6",
				    "name":"John",
				    "type": "User"
			     },
                           "additionalInfo":{
                               "group":{
                                   "id":"123434"
                                   "name":"Test"
				},
			        "groupRole":"admin",
			       "activity":{
                                   "id":"do_12443",
                                   "type": "Course",
                                   "name":"Math's Activity"  
				}
		   	 }
                            
                    },
                    "createdOn": 1620626043127
                }
            ]
        }
    }
}
```

