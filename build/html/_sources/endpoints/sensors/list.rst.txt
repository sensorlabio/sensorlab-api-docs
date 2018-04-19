.. http:get:: /api/v1/sensors

    **Request**:

    .. sourcecode:: http

        GET /api/v1/sensors HTTP/1.1
        Host: staging.sensorlab.io
        Accept: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {
            "result": [
                {
                    "id": "5ab8b113fc10152c70cdeb65",
                    "uniqueid": "93c55c3e-3ef4-4de6-9a8e-db5019b4a941",
                    "imei": "863911091619316",
                    "name": "Esta"
                },
                {
                    "id": "5ab8b113fc10152c70cdeb66",
                    "uniqueid": "876cc47b-5379-40de-83d0-10cf96720566",
                    "imei": "980098461327809",
                    "name": "Christelle"
                }
            ],
            "count": 200,
            "pages": 4
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: text/plain

        Unauthorized

    :query page: used for pagination. Default is 1.
    :query name: filter by name. Search is case-insensitive and searches using `like`.
    :query imei: filter by imei. Will search by exact match.
    :query uniqueid: filter by uniqueid. Will search by exact match.
    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.