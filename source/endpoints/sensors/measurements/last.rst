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
            "id": "5ab8d7effa631a239c2b1ae7",
            "sensor": "5ab8b113fc10152c70cdebbb",
            "type": "UDX",
            "value": [
                6.625,
                8.893,
                9.414
            ],
            "recieved": "2017-06-15T11:20:43.940Z",
            "created": "2018-03-26T11:22:23.828Z",
            "measurementgroup": "7b9dca62-47c2-488b-9ad2-66f394c43243"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :query type: filter by type.
    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.