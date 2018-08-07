Delete application
~~~~~~~~~~~~~~~~~~

.. http:get:: /api/v1/applications/(id)

    **Request**:

    .. sourcecode:: http

        DELETE /api/v1/applications/93cf3f40-9a16-11e8-9eb6-529269fb1459 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Application deleted."
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 404: Application not found

.. note:: We don't actually delete any data, just hide it.

.. note::
    Available for:

    - User token