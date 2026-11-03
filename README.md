# Literae Releases

Literae 桌面版的公开安装包、校验值与发行清单。

> 本仓库仅用于公开分发安装包，不包含 Literae 主程序源代码。仓库公开不代表 Literae 主程序已经采用开源许可证。

## 下载说明

正式版本将在本仓库的 **Releases** 页面提供：

| 平台 | 架构 | 文件 |
| --- | --- | --- |
| macOS | Apple Silicon / arm64 | `.dmg` |
| macOS | Intel / x64 | `.dmg` |
| Windows 10/11 | x64 | `.exe` |

每个版本同时提供 SHA-256 校验值和 `release-manifest.json`。请只下载与设备架构匹配的安装包。

## 本地 OCR

发行版计划内置 PP-OCRv6 small、ONNX Runtime 与 Literae 验证过的运行组件。安装后可直接使用本地 OCR，不要求 API Key；只有用户明确启用在线 API 回退时，页面才可能发送给配置的在线服务。

## 发布要求

只有同时满足以下条件的安装包才可标记为正式版本：

- 模型文件大小与 SHA-256 完整校验通过；
- 从安装包实际安装后，本地 `OCR123` 推理通过；
- 安装包架构与标注一致；
- Google Drive v3 离线发现资源可加载；
- 不包含用户文档、数据库、日志、设置、API Key 或签名私钥；
- macOS 完成 Developer ID 签名与公证，Windows 正式版完成 Authenticode 签名。

未签名或仅用于工程验证的构建必须标记为 **Pre-release**，不得替代正式版本。

## 校验下载

macOS：

```bash
shasum -a 256 <安装包.dmg>
```

Windows PowerShell：

```powershell
Get-FileHash <安装包.exe> -Algorithm SHA256
```

问题反馈请注明 Literae 版本、操作系统版本和设备架构，但不要上传含隐私内容的文档、API Key、数据库或日志。
