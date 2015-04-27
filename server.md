# In your Server

## Requeriments

* [NPM](https://npmjs.com/)
* [NodeJs](https://nodejs.org/) or [iojs](https://iojs.org/)

## Start & Configuration

Start with nodejs/iojs

```js
var io = require('socket.io')(SERVER, OPTS);
```

### SERVER

Is the instace for `http`

```js
var app = express();
var server = require('http').createServer( app );
```

### OPTS

Is a `Object` or `null`

- `allowRequest` (`Function`): A function that receives a given handshake or upgrade request as its first parameter, and can decide whether to continue or not. The second argument is a function that needs to be called with the decided information: `fn(err, success)`, where `success` is a boolean value where false means that the request is rejected, and err is an error code.
- `allowUpgrades` (`Boolean`): whether to allow transport upgrades (`true`)
- `browser client gzip` (`Boolean`): is the compress. (`false`)
- `cookie` (`String|Boolean`): name of the HTTP cookie that contains the client sid to send as part of handshake response headers. Set to `false` to not send one. (`io`)
- `httpCompression` (`Object|Boolean`): parameters of the http compression for the polling transports (see [zlib](http://nodejs.org/api/zlib.html#zlib_options) api docs). Set to `false` to disable. (`true`)
- `log colors` (`Boolean`): is de color for logs. (`true`)
- `log level` (`Number`): is de levels for logs.
- `match origin protocol` (`Boolean`): is for match protocol. (`false`)
- `maxHttpBufferSize` (`Number`): how many bytes or characters a message can be when polling, before closing the session (to avoid DoS). Default value is `10E7`.
- `origins` (`String`): start the connections. (`"*:*"`)
- `path` (`String`): is the path with connection start. (`/`)
- `perMessageDeflate` (`Object|Boolean`): parameters of the WebSocket permessage-deflate extension (see [ws module](https://github.com/einaros/ws) api docs). Set to `false` to disable. (`true`)
- `pingInterval` (`Number`): how many ms before sending a new ping packet (`25000`)
- `pingTimeout` (`Number`): how many ms without a pong packet to consider the connection closed (`60000`)
- `serveClient` (`String`): is the static files for SocketIO. (`false`)
- `threshold` (`Number`): data is compressed only if the byte size is above this value (`1024`)
- `transports` (`<Array> String`): transports to allow connections to (`['polling', 'websocket']`)


## Auth

```js
io.set('authorization', function(data, accept){
	accept(null, true);
});

```
- `data` (`Object`) : Is the data with the connection.
- `accept` (`function`) : Arguments
	- `Error` (`Error|null`) : Is the error when connection or a null
	- `Boolean` (`Boolean`) : Is connect

## Use
```js
io.use(function (data, next){
	next();
});
```

- `data` (`Object`) : Is the socket.
- `accept` (`function`) : Arguments
	- `Error` (`Error|null`) : Is the error when connection or a null


## Events

This is a example for events

```js
io.sockets.on('connection', function (socket){
	socket.emit('test', 'Data for the event');
	socket.on('news', function(data){
		console.log(data);
	});
	socket.on('disconnect', function(){
		console.log('The connections is close :(');
	});
});
```