# Changelog

All notable changes to `@orbitconnect/react-native` will be documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.1.1] — 2025-04-27

### Fixed
- Corrected API base URL from `orbitxyz.muvle.org` to `api.orbitconnect.cloud`
- Removed leaked Google Maps API key from published package (`src/.env`)
- Fixed TypeScript build errors (`absoluteFillObject`, `RTCSessionDescriptionInit`, lucide icon types)

### Changed
- Updated repository URL to `github.com/core-dynamics/orbitconnect-sdk`
- README now links to [orbitconnect.cloud](https://orbitconnect.cloud) for account creation
- Android test files excluded from published package
- Declaration maps (`.d.ts.map`) excluded from published package

---

## [0.1.0] — 2025-04-27

Initial public release.

### Added

**Core**
- `OrbitProvider` — root context provider with WebSocket lifecycle, token refresh (`onTokenExpired`), and theming
- `ApiClient` — typed HTTP client with automatic auth headers and error handling (`OrbitClientError`)

**Widgets**
- `Chat` — full-featured chat UI: conversation list, message bubbles, composer, reactions, reply/quote, file/image/video/audio attachments, voice recording, emoji & sticker picker, message search, pin, batch select/delete/forward, presence, call history
- `VideoCall` — floating WebRTC call overlay, renders automatically when a call is active
- `MeetingWidget` — full video-conferencing room with participant grid, screen share, reactions, and hand-raise

**Hooks**
- `useMessages` — real-time messages with typing indicators, pinned messages, read receipts, reactions, recall, edit
- `useConversations` — conversation list with live presence, typing, and delivery status
- `useCall` — full call lifecycle: initiate, accept, reject, end, mute, camera toggle, switch camera
- `useMeeting` — meeting lifecycle: join, leave, mute, screen share, raise hand, reactions
- `useAudioRecorder` — voice message recording with waveform amplitude sampling and cancel support
- `useMedia` — file upload, voice recording upload, upload-and-wait for server processing, download URL
- `useNotifications` — in-app notification feed with unread count, mark read, clear
- `usePresence` — real-time presence status per user (`online` / `away` / `offline`)
- `useCallHistory` — paginated call records with caller/callee info
- `useRealtime` — session lifecycle with transitions (chat → call → meeting)
- `useWebRTC` — low-level WebRTC hook for custom call UIs (offer/answer/ICE, mute, camera, switch camera)
- `useMeetingWebRTC` — full-mesh WebRTC for custom meeting UIs with per-participant peer connections
- `useRecording` — server-side call/meeting recording toggle with recording list
- `useSound` — system ringtone + notification sounds with custom URL override
- `useAppBrand` — resolves brand node from `AppConfig` (name, logo, flags)
- `usePushToken` — registers FCM (Android) / VoIP PushKit (iOS) token with the backend automatically

**Background & push**
- `initCallKeep` — CallKit (iOS) / ConnectionService (Android) setup
- `showIncomingCallNotification` — full-screen incoming call notification via Notifee (Android)
- `handleIncomingPush` — unified push payload handler for FCM and APNs
- `registerBackgroundCallNotificationHandler` — headless JS handler for background FCM messages
- `showMissedCallNotification`, `clearMissedCallBadge`, `showAppNotification`
- `getInitialCallNotification` — retrieve call data when app is cold-started from a push
- `requestFullScreenIntentPermission` — Android 14+ full-screen intent permission prompt
- `setCallNotificationTheme` — customize incoming call notification colors and labels (Android)
- `backgroundService` / `useBackgroundServiceStatus` / `registerBackgroundCallHandler` — legacy background service (deprecated, use CallKeep)

**Socket**
- `useOrbitEvent` — subscribe to any raw WebSocket event
- `useOrbitListener` — access the raw socket and connection status
- `OrbitListenerProvider` — standalone WebSocket provider (used internally by `OrbitProvider`)
- `OrbitSocket` — low-level WebSocket class
- `resolveWsUrl` — utility to build the WebSocket URL

**Theme**
- `ThemeProvider`, `useTheme`, `darkTheme`, `lightTheme`
- Full token set: backgrounds, foregrounds, bubbles, composer, borders, radii, fonts

**Native modules**
- Android: `OrbitConnectRNModule` (ringtone/notification sounds via `RingtoneManager`), `OrbitBackgroundModule` + `OrbitBackgroundService` (foreground WebSocket service), `OrbitCallActivity` (full-screen call UI over lock screen), `OrbitBootReceiver` (service restart on boot)
- iOS: `OrbitBackground` (background URLSession WebSocket + CallKit `CXProvider`), `OrbitConnectRN` (system sounds via `AudioServicesPlaySystemSound`)

---

[0.1.0]: https://github.com/core-dynamics/orbitconnect-sdk/releases/tag/v0.1.0
