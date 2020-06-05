# Delete sensor alert configuration


### DELETE (/api/v1/sensor/(id/alerts/(id)
**Request**:

```
DELETE /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts/6cc44ad0-c635-11e8-bf95-1dddf61566fa HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "success": true,
    "code": 100,
    "message": "Sensor alert deleted."
}
```


* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensor_alert.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


**Possible validation errors and codes:**


* code=2 - field=sensor - sensor field should be a correct UUID format


* code=4 - field=id - id field should be a correct UUID format

**NOTE**: Available for:


* User token


* Application token
