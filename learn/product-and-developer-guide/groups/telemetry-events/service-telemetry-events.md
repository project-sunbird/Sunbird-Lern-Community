# Service Telemetry Events

### List of Events <a href="#list-of-events" id="list-of-events"></a>

<details>

<summary>Audit Event</summary>

```
"edata": {
    "type": "group-created",
    "pageid": "groups-list",
    "props": [
      "name",
      "description"
    ],
    "currentstate": "active"
  }
```



</details>

<details>

<summary>Error Event</summary>

```
"edata": {
    "errtype": "GROUP_NOT_FOUND",
    "stackTrace": "org.sunbird.service.GroupServiceImpl.readGroup(GroupServiceImpl.java:76)org.sunbird.actors.UpdateGro",
    "error": "group does not exist with this group Id 7aa56a86-sc088-4d88-bddb-7f766469d063."
  }
```



</details>

<details>

<summary>Log Event</summary>

```
"edata": {
    "level": "TRACE",
    "requestId": "b45c38b7ac160bea1524d72614150a18",
    "context": null,
    "type": "system",
    "message": "ENTRY LOG: method : PATCH, url: /v1/group/update , For Operation : updateGroup",
    "params": [
      {
        "name": "", // name of the user
        "groupId": "7aa56a86-c088-4d88-bddb-7f766469d063"
      },
      {
        "channel": "01285019302823526477"
      },
      {
        "method": "PATCH"
      },
      {
        "msgId": "b45c38b7ac160bea1524d72614150a18"
      },
      {
        "telemetry_pdata_ver": "4.0.0"
      },
      {
        "actorId": "a10d5216-6b96-404c-8d1c-cc1f720d910a"
      },
      {
        "telemetry_pdata_pid": "groups-service"
      },
      {
        "actorType": "User"
      },
      {
        "url": "/v1/group/update"
      },
      {
        "X-Request-ID": "b45c38b7ac160bea1524d72614150a18"
      },
      {
        "env": "groups"
      },
      {
        "requestType": "API_CALL"
      },
      {
        "requestId": "b45c38b7ac160bea1524d72614150a18"
      },
      {
        "telemetry_pdata_id": "dev.sunbird.groups.service"
      },
      {
        "userId": "a10d5216-6b96-404c-8d1c-cc1f720d910a"
      }
    ]
  }
```



</details>



### Sample Telemetry Data

<details>

<summary>Audit Event Data</summary>

```
{
  "eid": "AUDIT",
  "ets": 1623220198975,
  "ver": "3.0",
  "mid": "ca0429c9b80ca5ceea8f5eaf377e287f",
  "actor": {
    "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
    "type": "User"
  },
  "context": {
    "channel": "01285019302823526477",
    "pdata": {
      "id": "dev.sunbird.groups.service",
      "pid": "groups-service",
      "ver": "4.0.0"
    },
    "env": "groups",
    "cdata": [
      {
        "id": "a10d5216-6b96-404c-8d1c-cc1f720d910a",
        "type": "User"
      },
      {
        "id": "d48d9259-1757-41f9-b81e-6b87b603756a",
        "type": "Groupid"
      },
      {
        "id": "ca0429c9b80ca5ceea8f5eaf377e287f",
        "type": "Request"
      }
    ],
    "rollup": {
      "l1": "01285019302823526477"
    }
  },
  "edata": {
    "type": "group-created",
    "pageid": "groups-list",
    "props": [
      "name",
      "description"
    ],
    "currentstate": "active"
  }
}
```

</details>

