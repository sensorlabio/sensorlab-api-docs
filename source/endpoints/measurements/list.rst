Get list of measurements
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/measurements

    **Request**:

    .. sourcecode:: http

        GET /api/v1/measurements HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "result": [
                {
                    "id": "5ab8d7effa631a239c2b1a4c",
                    "sensor": "5ab8b113fc10152c70cdebbd",
                    "type": "KVF",
                    "value": [
                        3.896,
                        4.037,
                        5.42
                    ],
                    "recieved": "2017-11-04T05:32:26.348Z",
                    "created": "2018-03-26T11:22:23.811Z",
                    "measurementgroup": "d25a3495-791a-47a1-b647-cc164a88973b"
                },
                {
                    "id": "5ab8d7effa631a239c2b1a50",
                    "sensor": "5ab8b113fc10152c70cdebce",
                    "type": "TTA",
                    "value": [
                        4.465,
                        4.126,
                        4.535
                    ],
                    "recieved": "2018-01-22T14:20:59.338Z",
                    "created": "2018-03-26T11:22:23.811Z",
                    "measurementgroup": "07f215ff-c3f2-47cc-84d2-dc67ae022859"
                },
            ],
            "count": 1000,
            "pages": 20
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