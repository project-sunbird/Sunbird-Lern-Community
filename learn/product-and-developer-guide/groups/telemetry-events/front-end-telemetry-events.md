# Front End Telemetry Events

### List of Events

<details>

<summary>Impression Event</summary>

```
"edata": {
    "type": "view", 
    "pageid": "explore-groups", // defines the event from which page
    "subtype": "paginate",
    "uri": "/explore-groups",
    "duration": 1.113
  }
```



</details>

<details>

<summary>Intract Event</summary>

```
 "edata": {
    "id": "groups-tab", 
    "type": "click", // action type
    "pageid": "groups" 
  }
```



</details>

<details>

<summary>Error Event</summary>

```
"edata": {
    "err": "CLIENT_ERROR", // defines the error
    "errtype": "ACTIVITY_ID_MISSING", // error type
    "stacktrace": "unhandled error",
    "requestid": "bdf1f139-6e39-47ad-860a-b5a9a5f07815", // message id
    "errmsg": [
      "GROUPS ActivityId is mandatory."
    ]
  }
```



</details>

### Sample Telemetry Data:

<details>

<summary>Error Event Data</summary>

```
{
  "eid": "ERROR",
  "ets": 1615202343313,
  "ver": "3.0",
  "mid": "ERROR:c72f604bd79d1827fb788e6f7dbca100",
  "actor": {
    "id": "anonymous",
    "type": "user"
  },
  "context": {
    "channel": "b00bc992ef25f1a9a8d63291e20efc8d",
    "pdata": {
      "id": "dev.sunbird.portal",
      "ver": "3.7.0"
    },
    "env": "groups",
    "sid": "AaT0pEut3m_7Xm2sEyDBZKtnhZnKLZpH",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [],
    "rollup": {
      "l1": "ORG_001",
      "l2": "b00bc992ef25f1a9a8d63291e20efc8d"
    }
  },
  "object": {},
  "tags": [
    "ORG_001",
    "b00bc992ef25f1a9a8d63291e20efc8d"
  ],
  "edata": {
    "err": "CLIENT_ERROR", // defines the error
    "errtype": "ACTIVITY_ID_MISSING", // error type
    "stacktrace": "unhandled error",
    "requestid": "bdf1f139-6e39-47ad-860a-b5a9a5f07815", // message id
    "errmsg": [
      "GROUPS ActivityId is mandatory."
    ]
  }
}
```



</details>
