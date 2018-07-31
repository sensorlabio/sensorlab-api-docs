Get single sensor
~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors/(id)

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors/5ab8b113fc10152c70cdeb65 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "id": "5ab8b113fc10152c70cdeb65",
            "uniqueid": "93c55c3e-3ef4-4de6-9a8e-db5019b4a941",
            "imei": "863911091619316",
            "name": "Esta",
            "application": "5b4f3e3d8ef5ae0a1473e1da",
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
    :>json string uniqueid: Sensor's Unique ID.
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