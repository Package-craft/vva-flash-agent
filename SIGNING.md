# VVA Android release signing

Certificate subject: `CN=VVA Release`  
Key: RSA, 3072 bits  
Certificate SHA-256: `82936336fba864be724267f0b5d35e8480d26a293901d4571abfd85cdfbc8046`

The release APK is signed with a dedicated release key and is not debuggable.
The key and password are not in this repository, APK or USB package. The exported
public certificate is not a private key.

To inspect an APK with Android SDK Build Tools:

```text
apksigner verify --verbose --print-certs VVA-0.1.77-preview.1.apk
```

Compare the signer with the official certificate, not merely the app name/icon.
The signature does not certify user-added toolbox files or guarantee that a host
computer is clean. This is Android APK signing, not Windows Authenticode signing
of every bundled script/runtime.

Old development builds use a different debug certificate. Do not uninstall an
existing test installation merely to bypass a signature conflict: that can lose
history and Keystore-protected data. Migration is a separate step; this release
preparation has not replaced any installed app.

Official reference: https://developer.android.com/studio/publish/app-signing
