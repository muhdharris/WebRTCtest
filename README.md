# Alpha Meet — WebRTC experiment

A peer-to-peer video call prototype built while learning how WebRTC actually works:
how a connection is negotiated, how media streams move without a server in the path,
and what has to happen before two browsers can see each other.

Built while studying Computer Systems & Networks — the point was to see the
signalling flow work, not to ship a product.

## What it demonstrates

- `RTCPeerConnection` negotiation between two browser peers
- `getUserMedia` for camera and microphone capture
- Media tracks added to the peer connection and streamed to the other side
- Connection state handling for ICE, connecting and connected phases

## Files

| File | Purpose |
|---|---|
| `index.html` | Markup for the call UI |
| `script.js` | Peer connection setup, media capture, event handlers |
| `styles.css` | Styling |

## Running it

WebRTC requires a secure context. `localhost` counts as secure, so a plain static
server is enough:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

**Note:** `getUserMedia` will prompt for camera and microphone access. On a machine
without a webcam the call will still negotiate, but you will get no video track.

## Why it exists

Reading the WebRTC spec leaves a lot of hand-waving about signalling. This was the
exercise for closing that gap — the answer is "a server, however small, has to exist
to introduce the peers, and everything after that is peer-to-peer".

## Licence

MIT — see [LICENSE](LICENSE).
