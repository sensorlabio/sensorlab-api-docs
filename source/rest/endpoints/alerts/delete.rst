Delete sensor alert configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:delete:: /api/v1/sensor/(id)/alerts/(id)

    **Request**:

    .. sourcecode:: http

        DELETE /api/v1/sensor/8dbc5460-9a18-11e8-9eb6-529269fb1459/alerts/6cc44ad0-c635-11e8-bf95-1dddf61566fa HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Sensor alert deleted."
        }

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensor_alert.
    :statuscode 401: User is not authorized - token is incorrect or outdated.

    **Possible validation errors and codes:**

    - code=2 - field=sensor - `sensor` field should be a correct UUID format
    - code=4 - field=id - `id` field should be a correct UUID format

.. note::
    Available for:

    - User token
    - Application token