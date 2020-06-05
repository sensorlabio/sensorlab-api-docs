# Public measurements namespace

You can receive measurements from public sensors using websockets.

In order to connect to websockets you should get public api key for your application.

When you have token you can connect to /measurements namespace:

```
let io = require('socket.io-client');

let socket = io('https://ws.test.sensorlab.io:8080/public?token='+token, {
    path: '/ws'
});
```

If your public api key is invalid, you will receive an error. You can catch it like this:

```
socket.on('error', function (reason) {
    reject(JSON.parse(reason));
    console.error('Unable to connect Socket.IO', reason);
});
```

You will receive error like this:

```
{code: 401, message: 'Authentication error. Please check your token.'}
```

When connected, you can join sensor rooms. There are 2 types of rooms:


* measurements for sensor


* measurements by type for sensor

Connect sensor room:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.emit('sensor', { sensor: sensor});
```

Connect sensor/type room:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.emit('sensor', { sensor: sensor, type: 'TMP'});
```

To leave room use this code:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.emit('sensor/disconnect', { sensor: sensor});
```

And to leave sensor/type room:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.emit('sensor/disconnect', { sensor: sensor, type: 'TMP'});
```

You can also leave all rooms at once:

```
this.socket.emit('sensor/disconnect/all');
```

If user/application with this token doesn’t have rights to the sensor or sensor is not public, a “sensor/access_denied” message will be emitted.

You can catch this message like this:

```
socket.on('sensor/access_denied', function(params) {
    console.log(params.sensor, params.message);
});
```

If there are no problems server will start emitting measurements and you can receive them with your client:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.on('measurements/' + sensor, (measurements) => {
    measurements.forEach((measurement) => {
        console.log(measurement.timestamp);
        console.log(measurement.type);
        console.log(measurement.value);
    });
});
```

To receive measurements from sensor/type room use this code:

```
let sensor = '7e9fb090-c717-11e8-b4d3-c587309ce935';
socket.on('measurements/' + sensor + '/TMP', (measurements) => {
    measurements.forEach((measurement) => {
        console.log(measurement.timestamp);
        console.log(measurement.type);
        console.log(measurement.value);
    });
});
```
