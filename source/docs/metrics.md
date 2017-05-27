title: Metrics
---
Moleculer has a metrics function. You can turn on it in the [broker options](#constructor-options) with `metrics: true` property.
If enabled, the broker emits metrics events in every `broker.call`. You can catch this events and transfer to your Tracer system (ZipKin, OpenTracing...etc)

### Request started event
The broker emit an `metrics.trace.span.start` event when a new call/request started.
The payload contains the following values:
```js
{ 
    // Context ID
	id: '4563b09f-04cf-4891-bc2c-f26f80c3f91e',
    // Request ID
	requestID: null,
    // Level of call
	level: 1,
    // Start time
	startTime: 1493903164726,
    // Is it a remote call
	remoteCall: false,
    // Called action
	action: { 
        name: 'v2.users.get' 
    }
    // Node ID of caller
    nodeID: "node-1",

    // Target nodeID if it's a remote call
    //targetNodeID: "node-2",

    // Parent context ID if it is a sub-call
    //parent: null
}
```

### Request finished event
The broker emit an `metrics.trace.span.finish` when a call/request finished.
The payload contains the following values:
```js
{ 
	// Context ID
    id: '4563b09f-04cf-4891-bc2c-f26f80c3f91e',
	// Request ID
    requestID: null,
	// Level of call
    level: 1,
	// Start time
    startTime: 1493903164726,
    // End time
    endTime: 1493903164731.3684,
    // Duration
	duration: 5.368304,
    // Is it a remote call
	remoteCall: false,
    // Is it resolved from cache
	fromCache: false,
	// Called action
    action: { 
		name: 'v2.users.get' 
	}
    // Node ID of caller
    nodeID: "node-1",

    // Target nodeID if it's a remote call
    //targetNodeID: "node-2",

    // Parent context ID if it is a sub-call
    //parent: null

    // Error if the call returned with error
    error: {
        name: "ValidationError",
        message: "Invalid incoming parameters"
    }
}
```