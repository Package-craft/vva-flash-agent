# Data and permissions

- There is no VVA account or VVA-hosted relay. Tasks, conversations and evidence are
  stored on the phone and/or the selected portable workspace.
- Requests sent to the configured model provider may contain task messages,
  selected documents, screenshots and tool outputs. That provider's terms apply.
- API credentials are held in Android Keystore-backed encrypted storage. USB
  pairing uses a one-time app-owned import file which is removed after import.
- Accessibility is for explicitly authorized phone control. The overlay, camera,
  notifications and exact alarms are used only for their corresponding features.
- The Windows companion listens on loopback and uses the authorized USB tunnel.
  It does not install a Windows service or add itself to startup.
- Tool evidence, transcripts and the used USB workspace may contain private data.
  Share a clean release package, not a copy of a used workspace.
- Bundled Google ML Kit OCR runs recognition on-device; its SDK may send operational
  metrics to Google under its terms. VVA is not described as having zero network
  traffic or zero third-party telemetry. See https://developers.google.com/ml-kit/terms.

Dependency notices and included MPL sources accompany the release packages.
