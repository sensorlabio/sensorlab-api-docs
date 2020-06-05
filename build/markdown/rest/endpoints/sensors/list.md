# Get sensors list


### GET (/api/v1/sensors()
**Request**:

```
GET /api/v1/sensors HTTP/1.1
Host: staging.sensorlab.io
Content-type: application/json
```

**Success response**:

```
HTTP/1.1 200 OK
Content-type: application/json

{
    "result": [
        {
            "id": "8dbc5460-9a18-11e8-9eb6-529269fb1459",
            "imei": "863911091619316",
            "name": "Esta",
            "application": "9c5b5c32-9a18-11e8-9eb6-529269fb1459",
            "batteryCharge": 27.7169,
            "isBatteryCharging": false,
            "isOnline": true
        },
        {
            "id": "876cc47b-5379-40de-83d0-10cf96720566",
            "imei": "980098461327809",
            "name": "Christelle",
            "application": "9c5b5fde-9a18-11e8-9eb6-529269fb1459",
            "batteryCharge": 6.7315,
            "isBatteryCharging": false,
            "isOnline": true
        }
    ],
    "count": 200,
    "pages": 4
}
```


* **Response JSON Object**

    
    * **id** (*string*) – Sensors’s ID.


    * **imei** (*string*) – Sensor’s IMEI.


    * **name** (*string*) – Sensor’s name.


    * **application** (*string*) – Application ID sensor is connected to.


    * **batteryCharge** (*number*) – Sensor’s battery charge in percent.


    * **isBatteryCharging** (*boolean*) – Indicates if battery is charging or not.


    * **isOnline** (*boolean*) – Indicates if sensor is online and sending data or not.


    * **is_public** (*boolean*) – Show if sensor is public or not.



* **Query Parameters**

    
    * **page** – used for pagination. Default is 1.


    * **name** – filter by name. Search is case-insensitive and searches using like.


    * **imei** – filter by imei. Will search by exact match.


    * **id** – filter by id. Will search by exact match.


    * **online_status** – pass “online” to search for online sensors or “offline” for offline sensors.


    * **battery_charge_min** – filter sensors by battery charge


    * **battery_charge_max** – filter sensors by battery charge


    * **sort** – sorting parameter.

    You must provide string with sorting field name and sorting type like this:

    > name,asc

    Available fields:


            * name - sort by sensor name

    Available sort types:


            * asc - Ascending sort


            * desc - Descending sort




* **Request Headers**

    
    * [Authorization](https://tools.ietf.org/html/rfc7235#section-4.2) – Bearer token from authentication.


    * [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) – application/json



* **Status Codes**

    
    * [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – No errors, will return result with sensors list.


    * [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – User is not authorized - token is incorrect or outdated.


    * [422 Unprocessable Entity](http://tools.ietf.org/html/rfc4918#section-11.2) – Validation error.


**Possible validation errors and codes:**


* code=1 - Sensor must be correct UUID format


* code=2 - online_status parameter must be online or offline


* code=3 - battery_charge_min must be an integer


* code=4 - battery_charge_max must be an integer


* code=5 - battery_charge_max should not be less than battery_charge_min


* code=6 - page must be an integer


* code=7 - next must be correct UUID format

**NOTE**: Available for:


* User token


* Application token

Application token will have access only to sensors assigned to this application.
