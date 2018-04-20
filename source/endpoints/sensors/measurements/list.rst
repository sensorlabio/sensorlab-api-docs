Get measurements for sensor
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/sensors/(id)/measurements

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors/5ab8b113fc10152c70cdeb65/measurements HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "result": [
                {
                    "id": "5ab8d7effa631a239c2b1a58",
                    "sensor": "5ab8b113fc10152c70cdeb65",
                    "type": "CZE",
                    "value": [
                        2.718,
                        6.263,
                        5.205
                    ],
                    "received": "2017-05-27T06:46:55.733Z",
                    "created": "2018-03-26T11:22:23.812Z",
                    "measurementgroup": "072b5d22-33d0-41e2-899f-a7c296f04edd"
                },
                {
                    "id": "5ab8d7effa631a239c2b1b6d",
                    "sensor": "5ab8b113fc10152c70cdeb65",
                    "type": "VJK",
                    "value": [
                        7.953,
                        7.688,
                        1.196
                    ],
                    "received": "2018-01-12T09:31:19.804Z",
                    "created": "2018-03-26T11:22:23.839Z",
                    "measurementgroup": "a0364248-e200-4f13-a5d0-29637f882b40"
                },
            ],
            "count": 5,
            "pages": 1
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :query page: used for pagination. Default is 1.
    :query type: filter by type.
    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.