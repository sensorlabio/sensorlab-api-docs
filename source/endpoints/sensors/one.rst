Get single sensor
~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors/(id)

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors/5ab8b113fc10152c70cdeb65 HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "id": "5ab8b113fc10152c70cdeb65",
            "uniqueid": "93c55c3e-3ef4-4de6-9a8e-db5019b4a941",
            "imei": "863911091619316",
            "name": "Esta"
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.