# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org)



### List of Events <a href="#list-of-events" id="list-of-events"></a>

<details>

<summary>Audit Event</summary>

```
"edata": {
    "state": "Create", // defines the state i.e: Mergecert, Mergeuser
    "props": [
      "certId", // certificate Id
      "userId"  // user Id
    ]
  }
```



</details>

<details>

<summary>Search Event</summary>

```
"edata": {
    "size": 1,
    "query": "", // serach query
    "filters": {
      "channel": "ORG_001" // filter based on channel or org
    },
    "sort": {},
    "type": "org",
    "topn": [
      {
        "id": "0126322873849692160"
      }
    ]
}
```



</details>

<details>

<summary>Error Event</summary>

```
"edata": {
    "err": null, // error
    "stacktrace": "org.sunbird.common.exception.ProjectCommonException.throwClientErrorException(ProjectCommonException",
    "errtype": null // error type
}
```



</details>

<details>

<summary>Log Event</summary>

```
"edata": {
    "level": "info",
    "type": "api_access", // type of event i.e: success event
    "message": "",
    "params": [
      {
        "duration": 65
      },
      {
        "method": "POST" // API Method type
      },
      {
        "url": "/v1/course/batch/create" // API
      },
      {
        "status": "200" // status code
      }
    ]
  }
```



</details>

