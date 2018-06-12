Get last measurement
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/measurements/last

    **Request**:

    .. sourcecode:: http

        GET /api/v1/measurements/last HTTP/1.1
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

    :query type: filter by type.
    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.