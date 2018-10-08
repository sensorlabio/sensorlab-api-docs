Alerts namespace
~~~~~~~~~~~~~~~~

You can receive alerts using websockets.

In order to connect to websockets you should generate correct JWT.

.. code-block:: javascript

    let api = new SensorlabApi();
    api.auth.application_token(public_api_key, private_api_key)
             .then((application_token) => {
                console.log(application_token);
             })
             .catch((response) => {
                console.log(response);
             });


When you have token you can connect to /alerts namespace:

.. code-block:: javascript

    let io = require('socket.io-client');

    let socket = io('https://ws.test.sensorlab.io:8080/alerts?token='+token, {
        path: '/ws'
    });

If your token is invalid, you will receive an error. You can catch it like this:

.. code-block:: javascript

    socket.on('error', function (reason) {
        reject(JSON.parse(reason));
        console.error('Unable to connect Socket.IO', reason);
    });

You will receive error like this:

.. code-block:: javascript

    {code: 401, message: 'Authentication error. Please check your token.'}

When connected, you can join sensor rooms.

Connect sensor room:

.. code-block:: javascript

    let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
    socket.emit('sensor', { sensor: sensor });

To leave room use this code:

.. code-block:: javascript

    let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
    socket.emit('sensor/disconnect', { sensor: sensor});

You can also leave all rooms at once:

.. code-block:: javascript

    this.socket.emit('sensor/disconnect/all');

If user/application with this token doesn't have rights to the sensor, a "sensor/access_denied" message will be emitted.

You can catch this message like this:

.. code-block:: javascript

    socket.on('sensor/access_denied', function(params) {
        console.log(params.sensor, params.message);
    });

If there are no problems server will start emitting alert and you can receive them with your client:

.. code-block:: javascript

    let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
    socket.on('alerts/' + sensor, (alerts) => {
        alerts.forEach((alert) => {
            console.log(alert.measurement.timestamp);
            console.log(alert.measurement.type);
            console.log(alert.measurement.value);

            console.log(alert.threshold.measurement_type);
            console.log(alert.threshold.threshold_type);
            console.log(alert.threshold.threshold_value);
        });
    });