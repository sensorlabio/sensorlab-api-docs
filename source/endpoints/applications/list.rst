Get list of applications
~~~~~~~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/applications

    **Request**:

    .. sourcecode:: http

        GET /api/v1/applications HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "result": [
                {
                    "id": "5af2cb517a6af41a20707965",
                    "name": "Sensors Application 1",
                    "description": "",
                    "created": "2018-05-09T10:20:01.352Z"
                },
                {
                    "id": "5af2cb4f7a6af41a20707964",
                    "name": "Sensors Application 2",
                    "description": "Application description",
                    "created": "2018-05-09T10:19:59.363Z"
                }
                ...
            ],
            "count": 27,
            "pages": 1
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :query page: used for pagination. Default is 1.
    :query name: search by name.
    :query sort: sorting parameter.

        You must provide string with sorting field name and sorting type like this:

                `type,asc`

        Available fields:
                - `name` - sort by creation date
                - `created` - sort by measurement type
        Available sort types:
                - `asc` - Ascending sort
                - `desc` - Descending sort

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.