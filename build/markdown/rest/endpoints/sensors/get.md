# Get single sensor


### GET (/api/v1/sensors/(id)
**Request**:

```
GET /api/v1/sensors/7765e032-9a18-11e8-9eb6-529269fb1459 HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "7765e032-9a18-11e8-9eb6-529269fb1459",
    "imei": "863911091619316",
    "name": "Esta",
    "application": "8078b94c-9a18-11e8-9eb6-529269fb1459",
    "batteryCharge": 6.7315,
    "isBatteryCharging": false,
    "isOnline": true,
    "is_public": false,
}
```


* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Response JSON Object**

    
    * **id** (*string*) – Sensors’s ID.


    * **imei** (*string*) – Sensor’s IMEI.


    * **name** (*string*) – Sensor’s name.


    * **application** (*string*) – Application ID sensor is connected to.


    * **batteryCharge** (*number*) – Sensor’s battery charge in percent.


    * **isBatteryCharging** (*boolean*) – Indicates if battery is charging or not.


    * **isOnline** (*boolean*) – Indicates if sensor is online and sending data or not.


    * **is_public** (*boolean*) – Show if sensor is public or not.



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensors list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Sensor not found


**NOTE**: Available for:


* User token


* Application token

Application token will have access only to sensors assigned to this application.
