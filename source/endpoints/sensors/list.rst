Get sensors list
~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "result": [
                {
                    "id": "5ab8b113fc10152c70cdeb65",
                    "uniqueid": "93c55c3e-3ef4-4de6-9a8e-db5019b4a941",
                    "imei": "863911091619316",
                    "name": "Esta",
                    "batteryCharge": 27.7169,
                    "isBatteryCharging": false,
                    "isOnline": true
                },
                {
                    "id": "5ab8b113fc10152c70cdeb66",
                    "uniqueid": "876cc47b-5379-40de-83d0-10cf96720566",
                    "imei": "980098461327809",
                    "name": "Christelle",
                    "batteryCharge": 6.7315,
                    "isBatteryCharging": false,
                    "isOnline": true
                }
            ],
            "count": 200,
            "pages": 4
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :>json string id: Sensors's ID.
    :>json string uniqueid: Sensor's Unique ID.
    :>json string imei: Sensor's IMEI.
    :>json string name: Sensor's name.
    :>json number batteryCharge: Sensor's battery charge in percent.
    :>json boolean isBatteryCharging: Indicates if battery is charging or not.
    :>json boolean isOnline: Indicates if sensor is online and sending data or not.

    :query page: used for pagination. Default is 1.
    :query name: filter by name. Search is case-insensitive and searches using `like`.
    :query imei: filter by imei. Will search by exact match.
    :query uniqueid: filter by uniqueid. Will search by exact match.
    :query sort: sorting parameter.

        You must provide string with sorting field name and sorting type like this:

                `name,asc`

        Available fields:
                - `name` - sort by sensor name
        Available sort types:
                - `asc` - Ascending sort
                - `desc` - Descending sort

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.