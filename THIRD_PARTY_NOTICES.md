# Third-party notices / 第三方告知

VVA's own distribution rules do not replace the licenses of Hermes or other
third-party software. The grants, attribution and source-code rights belonging to
those components remain intact. The table below identifies the runtime artifacts
and Python distributions included by this build; multiple rows can represent the
same distribution for different Android ABIs. `metadata only` means package
metadata was present without a matching Python payload.

VVA 自有部分暂不开放开发源码；这不限制第三方开源组件的原有权利。
告知文件随 APK 的 `assets/notices/` 和完整 U 盘包的 `notices/` 一起提供。

## Component families

- Hermes: MIT, Nous Research; original notice in `licenses/Hermes/LICENSE`.
- KaTeX and Marked: MIT; original notices in `licenses/KaTeX/` and `licenses/Marked/`.
- Chaquopy 17.2.0: MIT; Python Android 3.13.16: PSF and included historical licenses.
- AndroidX, Kotlin and other Apache dependencies: Apache-2.0, with original
  notices where supplied and the common license in `licenses/common/Apache-2.0.txt`.
- Google ML Kit / Play Services: the SDK terms linked per component apply.
  Bundled `third_party_licenses` files are preserved per artifact, not overwritten
  by another dependency with the same filename.
- Android Platform-Tools 37.0.1 and Windows CPython 3.14.7: the USB package retains
  `platform-tools/NOTICE.txt` and `runtime/python/LICENSE.txt` respectively.
  These runtime terms are not replaced by VVA's redistribution layout.
- Python's upstream third-party license appendix and the bundled OpenSSL 3.5.9
  license are included under `licenses/CPython-Android-native/`.
- The optional tool catalog contains download links, not redistributed Sysinternals,
  Geek, antivirus or other vendor executables. Their own terms apply on download.

ML Kit performs OCR on-device; its SDK can send operational metrics to Google.
See https://developers.google.com/ml-kit/terms and VVA's privacy notice.

## MPL source access / MPL 对应源码

The following source archives are included alongside these notices. They are
third-party source, not the VVA application development repository. MPL-licensed
files retain their MPL rights, including modification and redistribution.
No VVA modifications to these three package payloads are introduced by this build.

- certifi 2026.10.23: `notices/sources/certifi-2026.10.23-source.zip` in the download package; [upstream archive](https://files.pythonhosted.org/packages/fd/11/b524cbd9bbdaca58608e4cf4053fd463417549e1959fa8d3aa18319f9555/certifi-2026.10.23.tar.gz).
- tqdm 4.70.0: `notices/sources/tqdm-4.70.0-source.zip` in the download package; [upstream archive](https://files.pythonhosted.org/packages/21/3b/6c24bec5be5e743ffd99576daa5cc077722fc7d5bbc00bd133fa0c698dc6/tqdm-4.70.0.tar.gz).
- pathspec 1.1.1: `notices/sources/pathspec-1.1.1-source.zip` in the download package; [upstream archive](https://files.pythonhosted.org/packages/5a/82/42f767fc1c1143d6fd36efb827202a2d997a375e160a71eb2888a925aac1/pathspec-1.1.1.tar.gz).

## Runtime inventory

Licenses are taken from the distributed license text, package metadata and resolved
Maven POMs (including inherited licenses). This is a build inventory, not a claim
that every transitive native symbol has been independently legally certified.

| Component | Version | License | Location / scope |
| --- | --- | --- | --- |
| aiofiles | 25.1.0 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| aiohappyeyeballs | 2.7.1 | OSI Approved :: Python Software Foundation License | vendor/python-deps/common |
| aiohttp | 3.14.5 | Apache-2.0 AND MIT | vendor/python-deps/common |
| aiosignal | 1.4.0 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| annotated-types | 0.8.0 | MIT | vendor/python-deps/common |
| anthropic | 0.125.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| anyio | 4.14.2 | MIT | vendor/python-deps/common |
| asyncstdlib | 3.14.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| attrs | 26.1.0 | MIT | vendor/python-deps/common |
| certifi | 2026.10.23 | OSI Approved :: Mozilla Public License 2.0 (MPL 2.0) | vendor/python-deps/common |
| cffi | 2.0.0 | MIT | vendor/python-deps/common |
| chaquopy-libyaml | 0.2.5 | MIT | vendor/python-deps/common |
| charset-normalizer | 3.4.7 | MIT | vendor/python-deps/common |
| click | 8.4.2 | BSD-3-Clause | vendor/python-deps/common |
| colorama | 0.4.6 | OSI Approved :: BSD License | vendor/python-deps/common |
| croniter | 6.0.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| cryptography | 50.0.1 | Apache-2.0 OR BSD-3-Clause | vendor/python-deps/common |
| distro | 1.9.0 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| docstring_parser | 0.18.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| fal_client | 1.0.1 | Apache-2.0 | vendor/python-deps/common |
| filelock | 4.2.4 | MIT | vendor/python-deps/common |
| fire | 0.7.1 | Apache-2.0 | vendor/python-deps/common |
| frozenlist | 1.8.0 | Apache-2.0 | vendor/python-deps/common |
| h11 | 0.16.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| httpcore | 1.0.9 | BSD-3-Clause | vendor/python-deps/common |
| httpcore2 | 2.13.1 | BSD-3-Clause | vendor/python-deps/common |
| httpx | 0.28.1 | OSI Approved :: BSD License | vendor/python-deps/common |
| httpx2 | 2.13.1 | BSD-3-Clause | vendor/python-deps/common |
| httpx-sse | 0.4.3 | MIT | vendor/python-deps/common |
| idna | 3.19 | BSD-3-Clause | vendor/python-deps/common |
| importlib_metadata | 8.7.1 | Apache-2.0 | vendor/python-deps/common |
| Jinja2 | 3.1.6 | OSI Approved :: BSD License | vendor/python-deps/common |
| jiter | 0.16.0 | MIT | vendor/python-deps/common |
| jsonschema | 4.26.0 | MIT | vendor/python-deps/common |
| jsonschema-specifications | 2025.9.1 | MIT | vendor/python-deps/common |
| markdown-it-py | 4.0.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| MarkupSafe | 3.0.3 | BSD-3-Clause | vendor/python-deps/common |
| mcp | 2.3.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| mcp-types | 2.3.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| mdurl | 0.1.2 | OSI Approved :: MIT License | vendor/python-deps/common |
| msgpack | 1.2.2 | Apache-2.0 | vendor/python-deps/common |
| multidict | 6.7.1 | Apache License 2.0 | vendor/python-deps/common |
| openai | 2.54.0 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| opentelemetry-api | 1.39.1 | Apache-2.0 | vendor/python-deps/common |
| packaging | 26.3 | Apache-2.0 OR BSD-2-Clause | vendor/python-deps/common |
| platformdirs | 4.9.4 | MIT | vendor/python-deps/common |
| propcache | 0.5.2 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| pycparser | 3.0 | BSD-3-Clause | vendor/python-deps/common |
| pydantic | 2.13.5 | MIT | vendor/python-deps/common |
| pydantic_core | 2.46.5 | MIT | vendor/python-deps/common |
| Pygments | 2.20.0 | BSD-2-Clause | vendor/python-deps/common |
| PyJWT | 2.15.1 | MIT | vendor/python-deps/common |
| python-dateutil | 2.9.0.post0 | OSI Approved :: BSD License; OSI Approved :: Apache Software License | vendor/python-deps/common |
| python-dotenv | 1.2.2 | BSD-3-Clause | vendor/python-deps/common |
| python-multipart | 0.0.32 | Apache-2.0 | vendor/python-deps/common (metadata only) |
| pytz | 2025.2 | OSI Approved :: MIT License | vendor/python-deps/common |
| PyYAML | 6.0.3 | OSI Approved :: MIT License | vendor/python-deps/common |
| referencing | 0.37.0 | MIT | vendor/python-deps/common |
| requests | 2.33.1 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| rich | 14.3.3 | OSI Approved :: MIT License | vendor/python-deps/common |
| rpds-py | 0.30.0 | MIT | vendor/python-deps/common |
| six | 1.17.0 | OSI Approved :: MIT License | vendor/python-deps/common |
| sniffio | 1.3.1 | OSI Approved :: MIT License; OSI Approved :: Apache Software License | vendor/python-deps/common |
| sse-starlette | 3.3.2 | BSD-3-Clause | vendor/python-deps/common |
| starlette | 1.3.1 | BSD-3-Clause | vendor/python-deps/common |
| tenacity | 9.1.4 | OSI Approved :: Apache Software License | vendor/python-deps/common |
| termcolor | 3.3.0 | MIT | vendor/python-deps/common |
| tqdm | 4.70.0 | MPL-2.0 AND MIT | vendor/python-deps/common |
| truststore | 0.10.4 | MIT | vendor/python-deps/common |
| typing_extensions | 4.16.0 | PSF-2.0 | vendor/python-deps/common |
| typing-inspection | 0.4.4 | MIT | vendor/python-deps/common |
| tzdata | 2026.1 | Apache-2.0 | vendor/python-deps/common |
| urllib3 | 2.8.0 | MIT | vendor/python-deps/common |
| uvicorn | 0.41.0 | BSD-3-Clause | vendor/python-deps/common |
| websockets | 17.1 | BSD-3-Clause | vendor/python-deps/common |
| yarl | 1.25.1 | Apache-2.0 | vendor/python-deps/common |
| zipp | 3.23.0 | MIT | vendor/python-deps/common |
| psutil | 7.1.3 | BSD-3-Clause | vendor/python-deps/arm64-v8a |
| psutil | 7.1.3 | BSD-3-Clause | vendor/python-deps/x86_64 |
| pathspec | 1.1.1 | OSI Approved :: Mozilla Public License 2.0 (MPL 2.0) | vendor/python-extra |
| prompt_toolkit | 3.0.52 | OSI Approved :: BSD License | vendor/python-extra |
| pypdf | 6.21.4 | BSD-3-Clause | vendor/python-extra |
| ruamel.yaml | 0.18.16 | MIT license | vendor/python-extra |
| snowballstemmer | 3.1.1 | BSD-3-Clause | vendor/python-extra |
| socksio | 1.0.0 | OSI Approved :: MIT License | vendor/python-extra |
| tomli_w | 1.2.0 | OSI Approved :: MIT License | vendor/python-extra |
| wcwidth | 0.2.13 | OSI Approved :: MIT License | vendor/python-extra |
| yt-dlp | 2026.10.26 | Unlicense | vendor/python-extra |
| androidx.activity:activity | 1.6.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.annotation:annotation-experimental | 1.3.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.annotation:annotation | 1.3.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.appcompat:appcompat-resources | 1.6.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.appcompat:appcompat | 1.6.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.arch.core:core-common | 2.1.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.arch.core:core-runtime | 2.1.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.collection:collection | 1.1.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.concurrent:concurrent-futures | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.core:core-ktx | 1.9.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.core:core | 1.9.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.core:core | 1.9.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.cursoradapter:cursoradapter | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.customview:customview | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.drawerlayout:drawerlayout | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.emoji2:emoji2-views-helper | 1.2.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.emoji2:emoji2 | 1.2.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.exifinterface:exifinterface | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.fragment:fragment | 1.3.6 | The Apache Software License, Version 2.0 | jvm |
| androidx.fragment:fragment | 1.3.6 | The Apache Software License, Version 2.0 | jvm |
| androidx.interpolator:interpolator | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-common | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-livedata-core | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-livedata-core | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-livedata | 2.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-process | 2.4.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-runtime | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-viewmodel-savedstate | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-viewmodel | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.lifecycle:lifecycle-viewmodel | 2.5.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.loader:loader | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.resourceinspection:resourceinspection-annotation | 1.0.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.savedstate:savedstate | 1.2.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.startup:startup-runtime | 1.1.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.tracing:tracing | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.vectordrawable:vectordrawable-animated | 1.1.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.vectordrawable:vectordrawable | 1.1.0 | The Apache Software License, Version 2.0 | jvm |
| androidx.versionedparcelable:versionedparcelable | 1.1.1 | The Apache Software License, Version 2.0 | jvm |
| androidx.viewpager:viewpager | 1.0.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.android.datatransport:transport-api | 2.2.1 | The Apache Software License, Version 2.0 | jvm |
| com.google.android.datatransport:transport-backend-cct | 2.3.3 | The Apache Software License, Version 2.0 | jvm |
| com.google.android.datatransport:transport-runtime | 2.2.6 | The Apache Software License, Version 2.0 | jvm |
| com.google.android.gms:play-services-base | 18.5.0 | Android Software Development Kit License | jvm |
| com.google.android.gms:play-services-basement | 18.4.0 | Android Software Development Kit License | jvm |
| com.google.android.gms:play-services-mlkit-text-recognition-chinese | 16.0.1 | ML Kit Terms of Service | jvm |
| com.google.android.gms:play-services-mlkit-text-recognition-common | 19.1.0 | ML Kit Terms of Service | jvm |
| com.google.android.gms:play-services-tasks | 18.2.0 | Android Software Development Kit License | jvm |
| com.google.android.odml:image | 1.0.0-beta1 | Android Software Development Kit License | jvm |
| com.google.firebase:firebase-annotations | 16.0.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.firebase:firebase-components | 16.1.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.firebase:firebase-encoders-json | 17.1.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.firebase:firebase-encoders | 16.1.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.guava:listenablefuture | 1.0 | The Apache Software License, Version 2.0 | jvm |
| com.google.mlkit:common | 18.11.0 | ML Kit Terms of Service | jvm |
| com.google.mlkit:text-recognition-bundled-common | 17.0.0 | ML Kit Terms of Service | jvm |
| com.google.mlkit:text-recognition-chinese | 16.0.1 | ML Kit Terms of Service | jvm |
| com.google.mlkit:vision-common | 17.3.0 | ML Kit Terms of Service | jvm |
| com.google.mlkit:vision-interfaces | 16.3.0 | ML Kit Terms of Service | jvm |
| javax.inject:javax.inject | 1 | The Apache Software License, Version 2.0 | jvm |
| org.jetbrains.kotlin:kotlin-stdlib-common | 1.7.10 | The Apache License, Version 2.0 | jvm |
| org.jetbrains.kotlin:kotlin-stdlib-jdk7 | 1.6.0 | The Apache License, Version 2.0 | jvm |
| org.jetbrains.kotlin:kotlin-stdlib-jdk8 | 1.6.0 | The Apache License, Version 2.0 | jvm |
| org.jetbrains.kotlin:kotlin-stdlib | 1.7.10 | The Apache License, Version 2.0 | jvm |
| org.jetbrains.kotlinx:kotlinx-coroutines-android | 1.6.1 | The Apache Software License, Version 2.0 | jvm |
| org.jetbrains.kotlinx:kotlinx-coroutines-core-jvm | 1.6.1 | The Apache Software License, Version 2.0 | jvm |
| org.jetbrains:annotations | 13.0 | The Apache Software License, Version 2.0 | jvm |
| Chaquopy | 17.2.0 | MIT | runtime |
| CPython Android | 3.13.16 | PSF-2.0 and included historical licenses | runtime |

Full machine-readable mapping: `components.json`; verbatim license and notice texts:
`licenses/`. Google-specific terms remain linked in the relevant entry.

References: https://www.mozilla.org/en-US/MPL/2.0/FAQ/ ;
https://chaquo.com/chaquopy/license/ ;
https://github.com/NousResearch/hermes-agent/blob/main/LICENSE
