Get last generated alerts for sensor
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensor/(sensor)/alerts/last

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensor/7e9fb090-c717-11e8-b4d3-c587309ce935/alerts/last HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

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

    :>json object measurement: Triggering measurement.
    :>json array measurement.value: Measurement value.
    :>json string measurement.id: Measurement ID.
    :>json number measurement.timestamp: Timestamp for measurement.
    :>json string measurement.sensor: Sensor ID.
    :>json string measurement.type: Measurement type.
    :>json object threshold: Triggered threshold/sensor alert configuration.
    :>json string threshold.id: Triggered sensor alert ID.
    :>json string threshold.measurement_type: Sensor alert's measurement type.
    :>json string threshold.threshold_type: Sensor alert's threshold type.
    :>json mixed threshold.threshold_value: Sensor alert's threshold value.


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