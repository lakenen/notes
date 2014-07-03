# Stephen Belanger

**The node event loop**
* callbacks are not magically async - need the event loop!
* async is not free
* be consistent - if something advertises asynchronosity, it should always be async
* process.nextTick happens before IO, so use setImmediate
