# myApp/config/sockets.js
### Purpose
This is a configuration file that allows you to customize the way your app talks to clients over Socket.IO. 

It provides transparent access to Sails' encapsulated pubsub/socket server for complete customizability. In it you can do things on the list below (and more!).

- Override onConnect/onDisconnect methods (server side)
- Set transport method
- Change Heartbeat Interval
- Change socket store

### More Info
> Socket.IO configuration options can be found [here](https://github.com/LearnBoost/Socket.IO/wiki/Configuring-Socket.IO).


<docmeta name="uniqueID" value="socketsjs106184">
<docmeta name="displayName" value="sockets.js">

```
/**
 * WebSocket Server Settings
 * (sails.config.sockets)
 *
 * These settings provide transparent access to the options for Sails'
 * encapsulated WebSocket server, as well as some additional Sails-specific
 * configuration layered on top.
 *
 * For more information on using Sails with Sockets, check out:
 * http://links.sailsjs.org/docs/config/sockets
 */

module.exports.sockets = {

  // This custom onConnect function will be run each time AFTER a new socket connects
  // (To control whether a socket is allowed to connect, check out `authorization` config.)
  // Keep in mind that Sails' RESTful simulation for sockets
  // mixes in socket.io events for your routes and blueprints automatically.
  onConnect: function(session, socket) {

    // By default, do nothing.

  },

  // This custom onDisconnect function will be run each time a socket disconnects
  onDisconnect: function(session, socket) {

    // By default: do nothing.
  },



  // `transports`
  //
  // A array of allowed transport methods which the clients will try to use.
  // The flashsocket transport is disabled by default
  // You can enable flashsockets by adding 'flashsocket' to this list:
  transports: [
    'websocket',
    'htmlfile',
    'xhr-polling',
    'jsonp-polling'
  ],



  // Use this option to set the datastore socket.io will use to manage rooms/sockets/subscriptions:
  // default: memory
  adapter: 'memory',


  // Node.js (and consequently Sails.js) apps scale horizontally.
  // It's a powerful, efficient approach, but it involves a tiny bit of planning.
  // At scale, you'll want to be able to copy your app onto multiple Sails.js servers
  // and throw them behind a load balancer.
  //
  // One of the big challenges of scaling an application is that these sorts of clustered
  // deployments cannot share memory, since they are on physically different machines.
  // On top of that, there is no guarantee that a user will "stick" with the same server between
  // requests (whether HTTP or sockets), since the load balancer will route each request to the
  // Sails server with the most available resources. However that means that all room/pubsub/socket
  // processing and shared memory has to be offloaded to a shared, remote messaging queue (usually Redis)
  //
  // Luckily, Socket.io (and consequently Sails.js) apps support Redis for sockets by default.
  // To enable a remote redis pubsub server:
  // adapter: 'redis',
  // host: '127.0.0.1',
  // port: 6379,
  // db: 'sails',
  // pass: '<redis auth password>'
  // Worth mentioning is that, if `adapter` config is `redis`,
  // but host/port is left unset, Sails will try to connect to redis
  // running on localhost via port 6379



  // `authorization`
  //
  // Global authorization for Socket.IO access,
  // this is called when the initial handshake is performed with the server.
  //
  // By default (`authorization: false`), when a socket tries to connect, Sails
  // allows it, every time.  If no valid cookie was sent, a temporary session will
  // be created for the connecting socket.
  //
  // If `authorization: true`, before allowing a connection, Sails verifies that a
  // valid cookie was sent with the upgrade request.  If the cookie doesn't match
  // any known user session, a new user session is created for it. (In most cases, the
  // user would already have a cookie since they loaded the socket.io client and th