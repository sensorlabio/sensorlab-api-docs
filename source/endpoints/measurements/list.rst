Get list of measurements
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/measurements

    **Request**:

    .. sourcecode:: http

        GET /api/v1/measurements?sensor_id=5ab8b113fc10152c70cdeb65 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

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
                    "created": "2018-03-26T11:22:23.811Z"
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
                    "created": "2018-03-26T11:22:23.811Z"
                },
            ],
            "next": "5b1e58bdf670201dd0272886",
            "prev": null
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :jsonparam string next: Next measurement. Used for pagination.
    :jsonparam string prev: Prev measurement. Used for pagination.

    :query sensor_id: Sensor's ID.
    :query next: Use `next` or `prev` fields from response to get next or previous page.
    :query type: filter by type.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with sensors list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.

    :statuscode 422: Validation error.

        **Possible validation errors and codes:**

        - `code=1` - `field=sensor_id` - `Please, provide sensor field. This cannot be empty.`.
        - `code=2` - `field=sensor_id` - `This is not correct id format.`.
        - `code=3` - `field=next` - `This is not correct id format.`.

.. note::
    Available for:

    - User token
    - Application token

    Application token will have access only to measurements of sensors assigned to this application.