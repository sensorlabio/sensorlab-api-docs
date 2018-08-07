Get last measurement for sensor
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors/(id)/measurements/last

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors/5ab8b113fc10152c70cdebbb/measurements/last HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "type": "UDX",
            "value": [
                6.625,
                8.893,
                9.414
            ],
            "timestamp": 1533627864
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :query type: filter by type.

    :>json string type: Measurement type.
    :>json string value: Array of values.
    :>json string timestamp: Timestamp for measurement.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to measurements of sensors assigned to this application.