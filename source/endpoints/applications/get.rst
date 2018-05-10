Get application
~~~~~~~~~~~~~~~

.. http:get:: /api/v1/applications/(id)

    **Request**:

    .. sourcecode:: http

        GET /api/v1/applications/5af1aa428a695630f4219713 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "id": "5af2cb517a6af41a20707965",
            "name": "Sensors Application 1",
            "description": "",
            "created": "2018-05-09T10:20:01.352Z"
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