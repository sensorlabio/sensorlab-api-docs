Get single sensor
~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors/(id)

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors/7765e032-9a18-11e8-9eb6-529269fb1459 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "id": "7765e032-9a18-11e8-9eb6-529269fb1459",
            "imei": "863911091619316",
            "name": "Esta",
            "application": "8078b94c-9a18-11e8-9eb6-529269fb1459",
            "batteryCharge": 6.7315,
            "isBatteryCharging": false,
            "isOnline": true
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json

    :>json string id: Sensors's ID.
    :>json string imei: Sensor's IMEI.
    :>json string name: Sensor's name.
    :>json string application: Application ID sensor is connected to.
    :>json number batteryCharge: Sensor's battery charge in percent.
    :>json boolean isBatteryCharging: Indicates if battery is charging or not.
    :>json boolean isOnline: Indicates if sensor is online and sending data or not.

    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Sensor not found

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to sensors assigned to this application.