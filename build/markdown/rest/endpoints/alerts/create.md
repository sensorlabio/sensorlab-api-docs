# Create sensor alert configuration


### POST (/api/v1/sensor/(sensor/alerts()
**Request**:

```
POST /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
    "threshold_type": "min",
    "measurement_type": "HUM",
    "threshold_value": 65.25
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "Sensor alert created",
    "sensor_alert": {
        "id": "b5550190-c63a-11e8-98c9-cf732fa3c579",
        "threshold_type": "min",
        "measurement_type": "HUM",
        "threshold_value": 65.25
    }
}
```

**Example request with threhsold_type=loc**:

```
POST /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json

{
    "threshold_type": "loc",
    "measurement_type": "LOC",
    "threshold_value": {
        "lat": 36.1812440939046,
        "lng": -101.84828589116029,
        "radius": 1000
    }
}
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "Sensor alert created",
    "sensor_alert": {
        "id": "b5550190-c63a-11e8-98c9-cf732fa3c579",
        "threshold_type": "loc",
        "measurement_type": "LOC",
        "threshold_value": {
            "lat": 36.1812440939046,
            "lng": -101.84828589116029,
            "radius": 1000
        }
    }
}
```


* **Request JSON Object**

    
    * **threshold_type** (*string*) – Threshold type.

    Possible values:


        * min - set minimum value and alert will be generated if value from sensor will be lower than this value


        * max - set maximum value and alert will be generated if value from sensor will be higher than this value


        * loc - threshold type for GPS coordinates. If location is out of radius from specified point - alert will be generated



    * **measurement_type** (*string*) – Measurement type to check.


    * **threshold_value** (*string*) – Threshold value to compare to.

    This parameter depends on the threshold_type.


        * for type min value should be a number.


        * for type max value should be a number.


        * for type loc value should be a JSON object with lat, lng and radius parameters. Example: {lat: 36.1812440939046, lng: -101.84828589116029, radius: 1000}




* **Response JSON Object**

    
    * **sensor_alert** (*object*) – New sensor alert object.


    * **sensor_alert.id** (*string*) – Sensor alert ID.


    * **sensor_alert.threshold_type** (*string*) – Threshold type.


    * **sensor_alert.measurement_type** (*string*) – Measurement type.


    * **sensor_alert.threshold_value** (*string*) – Threshold value.



* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensor_alert.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=2 - field=sensor - sensor field should be a correct UUID format


* code=3 - field=threshold_type - threshold_type is required


* code=4 - field=threshold_type - threshold_type must be min, max or loc


* code=5 - field=measurement_type - measurement_type is required


* code=6 - field=threshold_value - threshold_value is required


* code=7 - field=threshold_value - threshold_value for threshold_type “min” must be a correct float


* code=8 - field=threshold_value - threshold_value for threshold_type “max” must be a correct float


* code=9 - field=threshold_value - threshold_value for threshold_type “loc” must be a correct JSON object with lat, lng and radius parameters


* code=10 - field=threshold_value - threshold_value.lat must be correct latitude


* code=11 - field=threshold_value - threshold_value.lng must be correct longitude


* code=12 - field=threshold_value - threshold_value.radius must be correct positive integer

**NOTE**: Available for:


* User token


* Application token
