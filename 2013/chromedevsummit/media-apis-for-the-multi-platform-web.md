Media APIs for the Multi-Platform Web

Sam Dutton and Jan Linden

http://simpl.info/

### Two trends:
* The rise of mobile
* Online media

### WebRTC
* talky.io demo (http://talky.io/chrome)
* 1000000000+ endpoints
* what do we need?
  * acquire a/v
  * estabilish a connection to peer
  * communicate a/v
  * communicate arbitrary data
* RTCPeerConnection does a lot
  * signal processing
  * codec handling
  * bandwidth mgmt
  * peer to peer communication
  * security
* RTCDataChannel
  * same API as WebSocket
  * ultra-low latency
  * optionally unreliable
  * sharefest demo

### Access local media
* `getUserMedia()`
* WebAudio
* WebMIDI

### Metadata
* in-band WebVTT: track data - one file contains video and subtitle tracks
* video alpha channel
