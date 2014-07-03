12 - Ingvar Stepanyan

JS in Binary

@rreverser

Data in JS
	array <- binary string
	CanvasPixelArray
	ArrayBuffer / typed arrays (Int32Array, etc)
	Buffer
	DataView

Binary Sources
	Remote URL (charset=x-user-defined, ArrayBuffer, Node.js)
	Local file (File API, Node.js)
	Data-URI (simple or base64-encoded)
	Stream (Node.js stream, WebSocket)

jDataView
	Spec types (Int8, Uint8, etc)
	Sequential write
	64-bit ints

jBinary
	High-level I/O for binary data

Wow, HTTP live streaming of video in JS/HTML5

Live coding demo
	load jDataView and jBinary
	load mp3 via File API + jbinary
	read data
	convert to data URI, play in audio tag
	read ID3 tag from mp3