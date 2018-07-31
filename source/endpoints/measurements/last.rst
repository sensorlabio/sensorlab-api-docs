Get last measurement
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/measurements/last

    **Request**:

    .. sourcecode:: http

        GET /api/v1/measurements/last?sensor_id=5ab8b113fc10152c70cdeb65 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "id": "5ab8d7effa631a239c2b1ae7",
            "sensor": "5ab8b113fc10152c70cdebbb",
            "type": "UDX",
            "value": [
                6.625,
                8.893,
                9.414
            ],
            "created": "2018-03-26T11:22:23.828Z"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized


    :query sensor_id: Sensor's ID.

    :query type: filter by type.
    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.

    :statuscode 422: Validation error.

       **Possible validation errors and codes:**

        - `code=1` - `field=sensor_id` - `Please, provide sensor field. This cannot be empty.`.
        - `code=2` - `field=sensor_id` - `This is not correct id format.`.

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to measurements of sensors assigned to this application.