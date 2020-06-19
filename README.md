# RustRCON
Rust RCON client for NodeJS


Usage
-----
```js
const { Client } = require('../src/index.js');

const rcon = new Client({
	ip: '192.0.0.1',
	port: '8080',
	password: '123',
	reconnectTimeout: 5000
});

rcon.login();

rcon.on('connected', () => {
	console.log(`Connected to ${rcon.ws.ip}:${rcon.ws.port}`);

	// Message, Name, Identifier.
	rcon.send('serverinfo', 'Artful', 10);

	setTimeout(() => {
		rcon.destroy();
	}, 5000);
});

rcon.on('error', err => {
	console.error(err);
});

rcon.on('disconnect', () => {
	console.log('Disconnected from RCON websocket');
});

rcon.on('message', message => {
	console.log(message);
});

```

## Credits
Kye [github](https://github.com/KyeNormanGill) for the original version <3
