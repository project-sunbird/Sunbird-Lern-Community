# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org)

### List of Events <a href="#list-of-events" id="list-of-events"></a>

**Front End Events**

<details>

<summary>Impression Event</summary>

```
"edata": {
    "type": "view",
    "pageid": "discussion-category",
    "uri": "/discussion-forum?categories=%7B%22result%22:%5B57%5D%7D&userName=cctn1350",
    "duration": 0.368
  }
```



</details>

<details>

<summary>Intract Event</summary>

```
"edata": {
    "id": "d.route",
    "type": "CLICK",
    "pageid": "discussion-home"
  }
```



</details>

<details>

<summary>Error Event</summary>

```
"edata": {
    "err": 400,
    "errtype": "DMW_FGCRT09",
    "requestid": "5f36c090-2eee-11eb-80ed-6bb70096c082",
    "errmsg": "Generalization of api failed"
  }
```



</details>

<details>

<summary>Trace Event</summary>

```
"edata": {
    "type": "api_call",
    "level": "TRACE",
    "message": "{\"title\":\"API Log\",\"url\":\"/discussion/tags\"}",
    "params": "[{\"title\":\"discussion-middleware\"},{\"category\":\"ENTRY LOG\"},{\"url\":\"/discussion/tags\"},{\"duration\":null},{\"status\":\"200\"},{\"protocol\":\"https\"},{\"method\":\"GET\"},{},{},{\"size\":15}]"
  }
```



</details>

#### Back End Events

<details>

<summary>Audit Event</summary>

```
{
  "eid": "AUDIT",
  "ets": "2022-01-04 03:23:26:681+0000",
  "ver": "1.0",
  "mid": "c86d6e107c3ac5d876e03619f2251552",
  "actor": {
    "id": "public",
    "type": "User"
  },
  "context": {
    "channel": "01269878797503692810",
    "pdata": {
      "id": "discussion-middleware",
      "pid": "staging.sunbird.portal",
      "ver": "4.6.0"
    },
    "env": "discussion-forum",
    "cdata": [],
    "rollup": {
      "l1": "01269878797503692810"
    }
  },
  "object": {},
  "edata": {
    "type": "downvote",
    "props": [
      "delta",
      "_uid"
    ]
  }
}
```

</details>

### Sample Telemetry Data

<details>

<summary>Trace Event Data</summary>

```
{
  "eid": "LOG",
  "ets": 1633931801927,
  "ver": "3.0",
  "mid": "LOG:ef8d3d0f662dbc5516b54abb98acd3ff",
  "actor": {
    "id": "anonymous",
    "type": "user"
  },
  "context": {
    "channel": "in.ekstep",
    "pdata": {
      "id": "discussion-middleware",
      "pid": "dev.sunbird.portal",
      "ver": "1.0.0"
    },
    "env": "discussion-middleware",
    "sid": "0ebkLX6MhVjhTsjJtoFaFhl5nZiPOnp2",
    "did": "1726023c0f4e4f17b2c956c412fd5859",
    "cdata": [],
    "rollup": {}
  },
  "object": {},
  "tags": [],
  "edata": {
    "type": "api_call",
    "level": "TRACE",
    "message": "{\"title\":\"API Log\",\"url\":\"/discussion/tags\"}",
    "params": "[{\"title\":\"discussion-middleware\"},{\"category\":\"ENTRY LOG\"},{\"url\":\"/discussion/tags\"},{\"duration\":null},{\"status\":\"200\"},{\"protocol\":\"https\"},{\"method\":\"GET\"},{},{},{\"size\":15}]"
  }
}
```

</details>

