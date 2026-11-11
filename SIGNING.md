# VVA Android release signing

Certificate subject: `CN=VVA Release`  
Key: RSA, 3072 bits  
Certificate SHA-256: `82936336fba864be724267f0b5d35e8480d26a293901d4571abfd85cdfbc8046`

The release APK is signed with a dedicated release key and is not debuggable.
The key and password are not in this repository, APK or USB package. The exported
public certificate is not a private key.

To inspect an APK with Android SDK Build Tools:

```text
apksigner verify --verbose --print-certs VVA-0.1.79-preview.1.apk
```

Compare the signer with the official certificate, not merely the app name/icon.
The signature does not certify user-added toolbox files or guarantee that a host
computer is clean. This is Android APK signing, not Windows Authenticode signing
of every bundled script/runtime.

The current candidate is **0.1.79-preview.1 (version code 79)**, for Android 11+.
Its APK manifest and release signature have been checked directly. The APK and
both complete USB packages contain the same signed application.

During revision 77 preparation, the USB import path passed on a release-signed,
non-debuggable sibling app on an actual Xiaomi phone, including credential
retrieval after process restart. This was not an installation of revision 79.
Revision 79's final phone installation and reply-copy check are still pending;
see its draft Release for the current acceptance status.

Old development builds use a different debug certificate. Do not uninstall an
existing test installation merely to bypass a signature conflict: that can lose
history and Keystore-protected data. Migration is a separate step; this release
preparation has not replaced any installed app.

Official reference: https://developer.android.com/studio/publish/app-signing
