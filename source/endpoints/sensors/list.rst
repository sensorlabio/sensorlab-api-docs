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

    :>json string id: Sensors's ID.
    :>json string imei: Sensor's IMEI.
    :>json string name: Sensor's name.
    :>json string application: Application ID sensor is connected to.
    :>json number batteryCharge: Sensor's battery charge in percent.
    :>json boolean isBatteryCharging: Indicates if battery is charging or not.
    :>json boolean isOnline: Indicates if sensor is online and sending data or not.
    :>json boolean is_public: Show if sensor is public or not.

    :query page: used for pagination. Default is 1.
    :query name: filter by name. Search is case-insensitive and searches using `like`.
    :query imei: filter by imei. Will search by exact match.
    :query id: filter by id. Will search by exact match.
    :query online_status: pass "online" to search for online sensors or "offline" for offline sensors.
    :query battery_charge_min: filter sensors by battery charge
    :query battery_charge_max: filter sensors by battery charge
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
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - code=1 - Sensor must be correct UUID format
    - code=2 - `online_status` parameter must be `online` or `offline`
    - code=3 - `battery_charge_min` must be an integer
    - code=4 - `battery_charge_max` must be an integer
    - code=5 - `battery_charge_max` should not be less than `battery_charge_min`
    - code=6 - `page` must be an integer
    - code=7 - `next` must be correct UUID format

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to sensors assigned to this application.