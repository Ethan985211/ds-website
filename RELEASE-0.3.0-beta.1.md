# DS Desktop 0.3.0-beta.1 — 首个发行候选

**日期：** 2026-09-21  
**版本：** 0.3.0-beta.1  
**许可：** 专有闭源 + EULA（见包内 `EULA.md`）  
**状态：** 候选 / 未代码签名 / 未完成干净机 D01–D20

## 双轨下载

| 轨道 | 资产文件 | 体积 | 说明 |
|------|----------|------|------|
| **轻量** | `DS-Desktop-0.3.0-beta.1-windows-x64-app.zip` | ~0.16 GB | 程序 + Electron + Web；首启引导下载/导入模型 |
| **完整离线** | `DS-Desktop-0.3.0-beta.1-windows-x64-offline.zip` | ~10.3 GB | 含 Ollama runtime + Qwen3:4b + bge-m3；可断网安装 |

- 完整包体积超过 GitHub 单附件 2 GiB 限制时，请通过网盘/R2 分发，官网 `window.DS_DOWNLOADS.full` 改为对应 URL。
- 轻量包适合挂 GitHub Releases 作为主下载。

## 轻量包安装

1. 解压 zip  
2. `powershell -ExecutionPolicy Bypass -File DS-Setup.ps1 -SkipModels -Shortcut`  
3. 启动桌面「Desktop system Agent」  
4. 若缺模型：首启页「下载模型到本机」或导入 model-pack 路径  

**依赖：** 本机需有 Ollama（或改用完整离线包）。

## 完整包安装

1. 解压 offline zip  
2. `powershell -ExecutionPolicy Bypass -File DS-Setup.ps1 -Shortcut`  
3. 启动桌面快捷方式  

## 校验（本地候选）

见仓库 `release/release_tracks.json` 与包内 `SHA256SUMS.txt` / `release_manifest.json`。

## 已知限制

- 未签名：Windows 可能提示未知发布者  
- Electron 壳 JS 已混淆；不宣称不可逆向  
- 默认模型仅 qwen3:4b + bge-m3（不含 gemma3 / qwen3.5）  
- PyMuPDF 已替换为 pypdf（BSD）  
- 官方下载以 GitHub Releases / 官网链接为准  

## 发布操作（维护者）

```powershell
# 有 gh 登录时
gh release create v0.3.0-beta.1 `
  "release/DS-Desktop-0.3.0-beta.1-windows-x64-app.zip#轻量应用包" `
  --title "DS Desktop 0.3.0-beta.1" `
  --notes-file docs/release/RELEASE-0.3.0-beta.1.md
```

或在 GitHub 网页：Releases → Draft → 上传 app zip → 发布 tag `v0.3.0-beta.1`。
