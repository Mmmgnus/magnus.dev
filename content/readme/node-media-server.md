---
title: "Node Media Server"
date: 2020-04-14T18:22:00+02:00
draft: false
---

# Media streaming with Node Media Server

Node Media Server is a Node.js implementation of RTMP/HTTP-FLV/WS-FLV/HLS/DASH/MP4 Media Server.

https://github.com/illuspas/Node-Media-Server

There is different ways to incorporate this library in your application, the recommended way is as a NPM dependency.

## Basic example on how to use Node Media Server:

First we need a folder,

```
> mkdir my-project-name
```

Then we initialize NPM so that we can install our dependencies.

```
> npm init
```

Time to install the node media server package from NPM

```
> npm install node-media-server
```

We are now ready to start writing some javascript code that will represent the media server.

```
const NodeMediaServer = require('node-media-server');

const config = {
  rtmp: {
    port: 1935,
    chunk_size: 60000,
    gop_cache: true,
    ping: 30,
    ping_timeout: 60
  },
  http: {
    port: 8000,
    allow_origin: '*'
  }
};

var nms = new NodeMediaServer(config)
nms.run();
```

Start the application

```
> node app.js
```

### How to start streaming
To test the media server we will need a video streaming application like OBS. Install it and open the settings. Find the tab called "Stream" and use the following settings:

```
Stream type: "Custom Streaming Server"
URL: "rtmp://localhost/live"
Stream key: <STREAM_NAME>
```

### How to view the stream
Download VLC, it's a media player that can handle anything! Navigate to `File -> Open network`, and insert the url `rtmp://localhost/live/<STREAM_NAME>`

