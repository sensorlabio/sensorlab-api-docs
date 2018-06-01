Create application
~~~~~~~~~~~~~~~~~~

.. http:post:: /api/v1/applications

    **Request**:

    .. sourcecode:: http

        POST /api/v1/applications/5af1aa428a695630f4219713 HTTP/1.1
        Host: staging.sensorlab.io
        Content-type: application/json

        {
            "name": "Application Name",
            "description": "Application Description"
        }

    **Success response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-type: application/json

        {
            "success": true,
            "code": 100,
            "message": "Application created.",
            "application": {
                "id": "5af404d28109aa2c846cd008",
                "name": "Application Name",
                "description": "Application Description",
                "token": "84786c221ccd87940ce84b1c7959f2e0955958c5e3070d5e1276aa65e28d822b3c9c83bb2d654d2c99b73d9604e8428d846e6a3874ef6d9c3e7113ac4a2f55e8"
            }
        }

    **Unauthorized response**

    .. sourcecode:: http

        HTTP/1.1 401 Unauthorized

        Unauthorized

    **Validation error response**

    .. sourcecode:: http

        HTTP/1.1 422 OK
        Content-type: application/json

        {
            "success": false,
            "code": 422,
            "message": "There are validation errors found.",
            "errors": [
                {
                    "code": 1,
                    "message": "Please, provide name field. This cannot be empty.",
                    "param": "name"
                }
            ]
        }

    :<json string name: Name for your application
    :<json string description: Description for your application

    :>json object application: Application data.
    :>json string application.id: Application ID.
    :>json string application.name: Application name.
    :>json string application.description: Application description.
    :>json string application.token: Generated token for application.
        Please note, that we don't save tokens and it will appear only once after app creation.
        You will be able to generate new one though.

    :reqheader Authorization: Bearer token from authentication.
    :reqheader Content-Type: application/json
    :statuscode 200: No errors, will return result with applications list.
    :statuscode 401: User is not authorized - token is incorrect or outdated.
    :statuscode 422: Validation error.


    **Possible validation errors and codes:**

    - `code=1` - `Please, provide name field. This cannot be empty`.