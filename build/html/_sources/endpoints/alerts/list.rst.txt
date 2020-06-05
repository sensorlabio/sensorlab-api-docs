List sensor alerts configurations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensor/(sensor)/alerts

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

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

    :>json string id: Sensor alert ID.
    :>json string threshold_type: Sensor alert threshold type.
    :>json string measurement_type: Sensor alert measurement type.
    :>json mixed threshold_value: Sensor alert value.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensor_alert.
    :statuscode 401: User is not authorized - token is incorrect or outdated.

    **Possible validation errors and codes:**

    - code=2 - field=sensor - `sensor` field should be a correct UUID format

.. note::
    Available for:

    - User token
    - Application token