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
                    "id": "d8d7f14a-9a16-11e8-9eb6-529269fb1459",
                    "name": "Sensors Application 1",
                    "description": "",
                    "created": "2018-05-09T10:20:01.352Z",
                    "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3",
                },
                {
                    "id": "f6ca0a08-9a16-11e8-9eb6-529269fb1459",
                    "name": "Sensors Application 2",
                    "description": "Application description",
                    "created": "2018-05-09T10:19:59.363Z",
                    "public_api_key": "sensorlab:application:cc7fddc2434a1773a360c84b1be71b16"
                }
            ],
            "count": 27,
            "pages": 1
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized
        Content-Type: applications/json

        {
            "success": false,
            "code": 401,
            "message": "Unauthorized"
        }

    :query page: used for pagination. Default is 1.
    :query name: search by name.
    :query sort: sorting parameter.
    :query show_deleted: if `true` - show deleted only applications.

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

    :>json string id: Application ID.
    :>json string name: Application name.
    :>json string description: Application description.
    :>json string public_api_key: Public API key.

    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 422: Validation error.

    **Possible validation errors and codes:**

    - code=1 - `page` must be an integer

.. note::
    Available for:

    - User token