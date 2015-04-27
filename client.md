# In your HTML

## Requeriments

* [socket.io-client](https://github.com/Automattic/socket.io-client)
* Ah... ¿HTML? & ¿Javascript?


## Start & Configuration

```html
<script src="/socket.io/socket.io.js"></script>
<script src="/public/myscript.js"></script>
```

```js
var socket = io(URL, OPTS);
```

### URL

Well... is a URL

Examples
```
https://localhost:3000/
localhost:3000
myapi.example.com:1000
ws://mychat.com
```

### OPTS

- `agent` (`http.Agent`): `http.Agent` to use, defaults to `false` (NodeJS only)
- `autoConnect` by setting this false, you have to call `manager.open` whenever you decide it's appropriate
- `ca` (`String`|`Array`): An authority certificate or array of authority certificates to check the remote host against.. Can be used in Node.js client environment to manually specify certificate information.
- `cert` (`String`): Public x509 certificate to use. Can be used in Node.js client environment to manually specify certificate information.
- `ciphers` (`String`): A string describing the ciphers to use or exclude. Consult the [cipher format list](http://www.openssl.org/docs/apps/ciphers.html#CIPHER_LIST_FORMAT) for details on the format.. Can be used in Node.js client environment to manually specify certificate information.
- `enablesXDR` (`Boolean`): enables XDomainRequest for IE8 to avoid loading bar flashing with click sound. default to `false` because XDomainRequest has a flaw of not sending cookie.
- `extraHeaders` (`Object`): Headers that will be passed for each request to the server (via xhr-polling and via websockets). These values then can be used during handshake or for special proxies. Can only be used in Node.js client environment.
- `forceBase64` (`Boolean`): forces base 64 encoding for polling transport even when XHR2 responseType is available and WebSocket even if the used standard supports binary.
- `forceJSONP` (`Boolean`): forces JSONP for polling transport.
- `jsonp` (`Boolean`): determines whether to use JSONP when necessary for polling. If disabled (by settings to false) an error will be emitted (saying "No transports available") if no other transports are available. If another transport is available for opening a connection (e.g. WebSocket) that transport will be used instead.
- `key` (`String`): Private key to use for SSL. Can be used in Node.js client environment to manually specify certificate information.
- `passphrase` (`String`): A string of passphrase for the private key or pfx. Can be used in Node.js client environment to manually specify certificate information.
- `path` (`String`): path to connect to, default is `/socket.io`
- `perMessageDeflate` (`Object|Boolean`): parameters of the WebSocket permessage-deflate extension (see [ws module](https://github.com/einaros/ws) api docs). Set to `false` to disable. (`true`)
- `pfx` (`String`): Certificate, Private key and CA certificates to use for SSL. Can be used in Node.js client environment to manually specify certificate information.
- `policyPort` (`Number`): port the policy server listens on (`843`)
- `randomizationFactor(`0.5`), 0 <= randomizationFactor <= 1 `timeout` connection timeout before a `connect_error` and `connect_timeout` events are emitted (`20000`)
- `reconnection` whether to reconnect automatically (`true`)
- `reconnectionAttempts` (`Infinity`) before giving up
- `reconnectionDelay` how long to initially wait before attempting a new reconnection (`1000`). Affected by +/- `randomizationFactor`, for example the default initial delay will be between 500 to 1500ms.
- `reconnectionDelayMax` maximum amount of time to wait between reconnections (`5000`). Each attempt increases the reconnection delay by 2x along with a randomization as above
- `rejectUnauthorized` (`Boolean`): If true, the server certificate is verified against the list of supplied CAs. An 'error' event is emitted if verification fails. Verification happens at the connection level, before the HTTP request is sent. Can be used in Node.js client environment to manually specify certificate information.
- `rememberUpgrade` (`Boolean`): defaults to false. If true and if the previous websocket connection to the server succeeded, the connection attempt will bypass the normal upgrade process and will initially try websocket. A connection attempt following a transport error will use the normal upgrade process. It is recommended you turn this on only when usingSSL/TLS connections, or if you know that your network does not block websockets.
- `timestampParam` (`String`): timestamp parameter (`t`)
- `timestampRequests` (`Boolean`): whether to add the timestamp with each transport request. Note: this is ignored if the browser is IE or Android, in which case requests are always stamped (`false`)
- `transports` (`Array`): a list of transports to try (in order).Defaults to `['polling', 'websocket']`. `Engine`always attempts to connect directly with the first one, provided the feature detection test for it passes.
- `upgrade` (`Boolean`): defaults to true, whether the client should try to upgrade the transport from long-polling to something better.

## Events

This is a example for events

```js
socket.on('connect', function(err){
	console.log('Error:', err );
});
socket.on('test', function(data){
	console.log('Event Test', data);
	socket.emit(news, {
		is : 'Is a example for test',
		hello : 'World'
	})
});
socket.on('disconnect', function(){
	console.log('Is close :(');
});

```