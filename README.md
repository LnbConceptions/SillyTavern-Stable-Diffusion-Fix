# SillyTavern Stable Diffusion Fix

这是一个修复版的 SillyTavern Stable Diffusion 扩展，添加了自动为 AI 角色消息生成图片的功能。

## 功能特性

- ✨ **自动图片生成**：AI 角色发送消息时自动生成相应的插图
- 🎯 **智能触发**：只对 AI 角色消息生成图片，不影响用户消息
- ⚙️ **可配置开关**：可以通过设置面板开启/关闭自动生图功能
- 🔧 **完全兼容**：基于原版 Stable Diffusion 扩展修改，保持所有原有功能

## 修改内容

相比原版 SillyTavern Stable Diffusion 扩展，本版本添加了以下功能：

1. **新增 `onCharacterMessageRendered` 函数**：处理 AI 角色消息渲染完成事件
2. **新增自动生图设置选项**：在设置面板中添加了 "Auto-generate images for AI messages" 复选框
3. **新增事件监听器**：监听 `CHARACTER_MESSAGE_RENDERED` 事件以触发自动生图
4. **优化图片保存逻辑**：生成的图片会自动保存到对应的消息气泡中

## 安装方法

### 方法一：直接替换文件（推荐）

1. 备份原有的 Stable Diffusion 扩展文件：
   ```bash
   cp public/scripts/extensions/stable-diffusion/index.js public/scripts/extensions/stable-diffusion/index.js.backup
   cp public/scripts/extensions/stable-diffusion/settings.html public/scripts/extensions/stable-diffusion/settings.html.backup
   ```

2. 下载本仓库的修改文件：
   ```bash
   wget https://raw.githubusercontent.com/LnbConceptions/SillyTavern-Stable-Diffusion-Fix/main/index.js
   wget https://raw.githubusercontent.com/LnbConceptions/SillyTavern-Stable-Diffusion-Fix/main/settings.html
   ```

3. 替换原有文件：
   ```bash
   cp index.js public/scripts/extensions/stable-diffusion/
   cp settings.html public/scripts/extensions/stable-diffusion/
   ```

4. 重启 SillyTavern

### 方法二：Git 克隆

1. 克隆本仓库：
   ```bash
   git clone https://github.com/LnbConceptions/SillyTavern-Stable-Diffusion-Fix.git
   ```

2. 复制文件到 SillyTavern 目录：
   ```bash
   cp SillyTavern-Stable-Diffusion-Fix/index.js /path/to/SillyTavern/public/scripts/extensions/stable-diffusion/
   cp SillyTavern-Stable-Diffusion-Fix/settings.html /path/to/SillyTavern/public/scripts/extensions/stable-diffusion/
   ```

## 使用方法

1. 确保已正确配置 Stable Diffusion 后端（ComfyUI 或 AUTOMATIC1111）
2. 在 SillyTavern 的扩展设置中找到 "Stable Diffusion" 扩展
3. 勾选 "Auto-generate images for AI messages" 选项
4. 开始与 AI 角色对话，系统会自动为 AI 的回复生成相应插图

## 技术说明

本修复版本通过以下方式实现自动生图功能：

- 监听 `CHARACTER_MESSAGE_RENDERED` 事件
- 检查消息来源是否为 AI 角色
- 检查自动生图功能是否启用
- 调用原有的图片生成逻辑
- 将生成的图片保存到消息中

## 兼容性

- ✅ SillyTavern 1.12.0+
- ✅ ComfyUI 后端
- ✅ AUTOMATIC1111 后端
- ✅ 所有原有 Stable Diffusion 扩展功能

## 问题反馈

如果遇到问题，请在 [Issues](https://github.com/LnbConceptions/SillyTavern-Stable-Diffusion-Fix/issues) 中反馈。

## 许可证

本项目基于原版 SillyTavern 的许可证条款发布。
