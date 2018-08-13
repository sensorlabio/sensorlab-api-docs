Get application
~~~~~~~~~~~~~~~

.. http:get:: /api/v1/applications/(id)

    **Request**:

    .. sourcecode:: http

        GET /api/v1/applications/d8d7f14a-9a16-11e8-9eb6-529269fb1459 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "id": "d8d7f14a-9a16-11e8-9eb6-529269fb1459",
            "name": "Sensors Application",
            "description": "Sensor Description",
            "created": "2018-05-09T10:20:01.352Z",
            "public_api_key": "sensorlab:application:62fa02f38ff6100dbbd1cdff2339ccf3"
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

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json

    :>json string id: Application ID.
    :>json string name: Application name.
    :>json string description: Application description.
    :>json string public_api_key: Public API key.

    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Application not found

.. note::
    Available for:

    - User token