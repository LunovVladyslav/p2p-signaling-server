# P2P Signaling Server

WebRTC signaling server built with Spring Boot 4 and WebSocket (STOMP).
Deployed on Render: https://p2p-signaling-server.onrender.com

## What it does

Acts as a signaling intermediary for peer-to-peer connections — 
coordinates WebRTC handshakes without handling media streams directly.

## Features

- **Peer management** — register, discover, auto-remove on disconnect
- **WebRTC signaling** — SDP and ICE candidate forwarding between peers
- **Call flow** — call request, answer, hangup signaling
- **Encrypted messaging** — relay encrypted messages between peers
- **Public channels** — create and broadcast to named channels
- **File transfer signaling** — coordinate P2P file transfers via WebRTC
- **JWT authentication** — register, login, biometric password reset
- **Admin panel** — ban users, manage channels, broadcast notifications

## WebSocket Endpoints (STOMP)

| Destination | Description |
|---|---|
| `/app/register` | Register peer |
| `/app/webrtc/sdp/{targetId}` | Forward SDP offer/answer |
| `/app/webrtc/ice/{targetId}` | Forward ICE candidate |
| `/app/call/{targetId}` | Initiate call |
| `/app/answer` | Answer call |
| `/app/hangup/{targetId}` | End call |
| `/app/message/{targetId}` | Send encrypted message |
| `/app/channel/register` | Create public channel |
| `/app/file/request/{targetId}` | Initiate file transfer |

## Stack

Java 21 · Spring Boot 4 · WebSocket (STOMP) · Spring Security  
JWT (jjwt 0.12.5) · JPA · H2 · Docker

## Run

```bash
git clone https://github.com/LunovVladyslav/p2p-signaling-server.git
cd p2p-signaling-server
docker-compose up
