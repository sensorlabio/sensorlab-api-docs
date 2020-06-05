# Get last generated alerts for sensor


### GET (/api/v1/sensor/(sensor/alerts/last()
**Request**:

```
GET /api/v1/sensor/7e9fb090-c717-11e8-b4d3-c587309ce935/alerts/last HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

[
    {
        "measurement": {
            "value": [
                48.213800963395784,
                15.13119759639926
            ],
            "id": "e224df91-c718-11e8-9ef1-39ba3cb4dad3",
            "timestamp": 1538577032000,
            "sensor": "7e9fb090-c717-11e8-b4d3-c587309ce935",
            "type": "LOC"
        },
        "threshold": {
            "id": "e1d38b44-c718-11e8-9ef1-39ba3cb4dad3",
            "measurement_type": "LOC",
            "threshold_type": "loc",
            "threshold_value": {
                "lat": 48.213641,
                "lng": 15.130691999999954,
                "radius": 25
            }
        }
    },
    {
        "measurement": {
            "value": [
                85.16
            ],
            "id": "e224df90-c718-11e8-9ef1-39ba3cb4dad3",
            "timestamp": 1538577032000,
            "sensor": "7e9fb090-c717-11e8-b4d3-c587309ce935",
            "type": "HUM"
        },
        "threshold": {
            "id": "e1d38b43-c718-11e8-9ef1-39ba3cb4dad3",
            "measurement_type": "HUM",
            "threshold_type": "max",
            "threshold_value": 60
        }
    },
    {
        "measurement": {
            "value": [
                20.25
            ],
            "id": "e224b883-c718-11e8-9ef1-39ba3cb4dad3",
            "timestamp": 1538577032000,
            "sensor": "7e9fb090-c717-11e8-b4d3-c587309ce935",
            "type": "TMP"
        },
        "threshold": {
            "id": "e1d38b42-c718-11e8-9ef1-39ba3cb4dad3",
            "measurement_type": "TMP",
            "threshold_type": "min",
            "threshold_value": 25
        }
    }
]
```


* **Response JSON Object**

    
    * **measurement** (*object*) – Triggering measurement.


    * **measurement.value** (*array*) – Measurement value.


    * **measurement.id** (*string*) – Measurement ID.


    * **measurement.timestamp** (*number*) – Timestamp for measurement.


    * **measurement.sensor** (*string*) – Sensor ID.


    * **measurement.type** (*string*) – Measurement type.


    * **threshold** (*object*) – Triggered threshold/sensor alert configuration.


    * **threshold.id** (*string*) – Triggered sensor alert ID.


    * **threshold.measurement_type** (*string*) – Sensor alert’s measurement type.


    * **threshold.threshold_type** (*string*) – Sensor alert’s threshold type.


    * **threshold.threshold_value** (*mixed*) – Sensor alert’s threshold value.



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
