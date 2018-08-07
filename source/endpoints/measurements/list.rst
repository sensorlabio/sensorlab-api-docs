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
                    "type": "KVF",
                    "value": [
                        3.896,
                        4.037,
                        5.42
                    ],
                    "timestamp": "1533627864"
                },
                {
                    "type": "TTA",
                    "value": [
                        4.465,
                        4.126,
                        4.535
                    ],
                    "timestamp": "1533627865"
                },
            ],
            "next": "d438a4b2-9a17-11e8-9eb6-529269fb1459",
            "prev": null
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :query sensor_id: Sensor's ID.
    :query next: Use `next` or `prev` fields from response to get next or previous page.
    :query type: filter by type.

    :>json string result.type: Measurement type.
    :>json string result.value: Array of values.
    :>json string result.timestamp: Timestamp for measurement.
    :>json string next: This param shows next measurement ID for next page. Use it with `next` query parameter.
    :>json string prev: This param shows prev measurement ID for prev page. Use it with `next` query parameter.

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