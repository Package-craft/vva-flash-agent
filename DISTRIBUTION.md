# VVA distribution rules — release preparation draft

VVA is currently free to use. Its development repository is not published. A decision to open source VVA later does not grant an open-source license today.

These rules concern the VVA-authored application and companion components only. Hermes and other third-party components retain their own licenses, notices and rights; these rules do not remove those rights.

## Official downloads

The official VVA repository provides the application package and the complete USB companion package. The complete USB package works after extraction and normal device authorization; no extra reconstruction step is imposed on official downloads.

## Redistribution layout

The authorized redistribution edition consists of both:

1. **Main package**: the original VVA APK and `usb-payload/`, containing all companion files except the two primary Start/Stop entry scripts.
2. **USB package**: only the two primary entry scripts (`启动.cmd` / `终止.cmd` in Chinese, or `Start.cmd` / `Stop.cmd` in English).

The recipient copies the contents of `usb-payload/` into the same directory as the two entry scripts, preserving subdirectories. The filenames and layout in the supplied edition must be retained. Local assembly by the recipient is allowed.

Redistributors must use the supplied redistribution edition without modifying the VVA components, adding installers/advertising/extra programs, charging for the files, removing attribution/signatures/notices, or representing their channel as the official VVA publisher. Link to the official repository and identify the release version. Do not redistribute personal workspaces, credentials, phone histories or downloaded third-party tool executables.

Users may customize their own tools, skills and local workspace. This does not make their additions official or grant permission to distribute a modified VVA edition. Third-party components remain governed by their own licenses, including any independent redistribution rights they grant.

This split is a distribution arrangement. It is not encryption, DRM, a malware scan or proof that an unofficial download is safe. The original signed APK remains unchanged in both editions.

## 中文说明

目前 VVA 免费使用，开发源码暂不公开。本约定仅适用于 VVA 自有部分，不限制 Hermes 或其他第三方许可证已经授予的权利。

- 官方：本体包 + 完整 U 盘包，正常解压使用。
- 转载：本体包内有原 APK 及 `usb-payload/`；U 盘包只有启动和终止两个主入口脚本。
- 接收者需把 `usb-payload/` 里面的文件复制到两个脚本旁边，保留目录结构；允许接收者在本地完成这一步。
- 转载使用提供的分装版本，不修改 VVA、不夹带安装器/广告/其他程序、不对文件收费、不删除声明或签名、不冒充官方，并标注版本和官方来源。
- 不转载私人工作区、密钥、手机对话或本地下载的第三方工具二进制。
- 用户可以定制自己使用的工具、技能和工作区；这些新增内容不因此成为官方内容。

该分装并非加密或防病毒机制。正式对外发布前确认本草案及第三方告知文件。
