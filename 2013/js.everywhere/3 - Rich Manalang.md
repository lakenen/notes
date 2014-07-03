3 - Rich Manalang

Making our web apps safely hackable

@rmanalan

3rd party JS widgets
	security risks
	page weight
	maintenance

hackable => extensible

JIRA
	completely extensible
	plugin framework

making our webapps extensible by 3rd parties, safely

3 capabilities
	access to REST APIs
	event notifications
	UI extensibility

Follow buttons
	not actually very simple
	"a ship in port is safe, but that's not what ships are built for"
	usually done through iframes for security
	security
		essential
		makes simple things difficult

For UI components
	ability for 3rd party to
		resize
		make requests
		send and listen to events

window.postMessage()
	full support not until IE 11 (<= 10 can only send strings)
	prone to resource contention
	solution: use channel messaging

MessageChannel
	establish a 2-way communication channel

options
	postMessage is IE8+ (partial support)
	easyXDM
	porthole
	oasis.js
	conductor.js

Oasis.js
	abstraction on top of postMessage
	safely embed 3rd party code
	sandboxing through iframe or webworker
	capability-based security
		as a host, you can tell the sandboxes exactly what capabilities you want to expose
	abstracting services, consumers, events, and requests
	async via promises
	wiretapping
		listen to all communication between all the sandboxes etc, makes it easy to debug

Conductor.js
	framework for building sandboxed apps
	gives 3rd parties a well-defined framework for building extensions
	built on top of oasis.js

Issues
	css can't cascade down to iframes (but there are hacks)
	relative links open in iframe
		hack/fix - use <base> tag
	dynamic resizing is hard