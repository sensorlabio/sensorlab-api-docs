# List sensor alerts configurations


### GET (/api/v1/sensor/(sensor/alerts()
**Request**:

```
GET /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

[
    {
        "id": "6cc44ad0-c635-11e8-bf95-1dddf61566fa",
        "threshold_type": "min",
        "measurement_type": "TMP",
        "threshold_value": -15
    },
    {
        "id": "6cfcbff0-c635-11e8-bf95-1dddf61566fa",
        "threshold_type": "max",
        "measurement_type": "HUM",
        "threshold_value": 80
    },
    {
        "id": "b5550190-c63a-11e8-98c9-cf732fa3c579",
        "threshold_type": "loc",
        "measurement_type": "LOC",
        "threshold_value": {
            "lat": 36.1812440939046,
            "lng": -101.84828589116029,
            "radius": 1000
        }
    }
]
```


* **Response JSON Object**

    
    * **id** (*string*) – Sensor alert ID.


    * **threshold_type** (*string*) – Sensor alert threshold type.


    * **measurement_type** (*string*) – Sensor alert measurement type.


    * **threshold_value** (*mixed*) – Sensor alert value.



* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensor_alert.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


**Possible validation errors and codes:**


* code=2 - field=sensor - sensor field should be a correct UUID format

**NOTE**: Available for:


* User token


* Application token
