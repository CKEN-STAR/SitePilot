# SitePilot v0.1.0 发布说明

## 🎉 首次发布

我们很高兴地宣布 SitePilot v0.1.0 正式发布！这是一款专为 Windows 平台设计的现代化桌面书签管理器。

---

## 📥 下载

### 选择适合您的版本

#### 🌟 绿色版（推荐）

**适合大多数用户**

- **文件：** [SitePilot_v0.1.0_Portable.zip](https://github.com/CKEN-STAR/SitePilot/releases/download/v0.1.0/SitePilot_v0.1.0_Portable.zip)
- **大小：** 6.93 MB
- **SHA256：** `待添加`
- **使用：** 解压后双击 `SitePilot.exe` 即可运行

#### 📦 安装程序

**需要开始菜单快捷方式的用户**

- **文件：** [SitePilot_0.1.0_x64-setup.exe](https://github.com/CKEN-STAR/SitePilot/releases/download/v0.1.0/SitePilot_0.1.0_x64-setup.exe)
- **大小：** ~20 MB
- **SHA256：** `待添加`
- **使用：** 双击运行，按照向导完成安装

#### 🏢 MSI 安装包

**企业部署和IT管理员**

- **文件：** [SitePilot_0.1.0_x64_en-US.msi](https://github.com/CKEN-STAR/SitePilot/releases/download/v0.1.0/SitePilot_0.1.0_x64_en-US.msi)
- **大小：** ~20 MB
- **SHA256：** `待添加`
- **使用：** 支持静默安装 `msiexec /i SitePilot_0.1.0_x64_en-US.msi /quiet`

---

## ✨ 主要功能

### 核心功能

#### 📌 书签管理
- ✅ 添加、编辑、删除书签
- ✅ 自动获取网站图标（5个备用源）
- ✅ 点击即可在默认浏览器打开
- ✅ 书签分类管理

#### 🎨 界面系统
- ✅ **4种布局模式**
  - Cards（卡片布局）- 经典网格展示
  - Carousel（轮播布局）- 横向滚动展示
  - Timeline（时间线布局）- 垂直时间线展示
  - Hexagon（六边形布局）- 独特六边形设计

- ✅ **5种主题**
  - Light（浅色主题）
  - Dark（深色主题）
  - Blue（蓝色主题）
  - Purple（紫色主题）
  - Green（绿色主题）

#### ⏱️ 特色功能
- ✅ 计时器功能（5种动画样式）
- ✅ 窗口状态记忆（大小、位置）
- ✅ 所有设置自动保存
- ✅ 本地数据存储，保护隐私

---

## 🎯 设计亮点

### 华丽动画

每种布局都有独特的动画效果：

- **Cards布局：** 浮动气泡背景 + 旋转图案悬停效果
- **Carousel布局：** 波浪流动背景 + 涟漪脉冲悬停效果
- **Timeline布局：** 粒子漂浮背景 + 旋转光环悬停效果
- **Hexagon布局：** 网格脉冲背景 + 六边形呼吸悬停效果

### 简约设计

- 淡雅的配色方案，不会造成视觉疲劳
- 清晰的层次结构
- 直观的操作流程
- 流畅的交互体验

### 性能优化

- 启动速度快（< 1秒）
- 内存占用低（< 100MB）
- 支持500+书签无卡顿
- 60fps 流畅动画

---

## 🔧 技术特性

### 技术栈

- **框架：** Tauri 2.x（轻量级桌面应用框架）
- **前端：** React 19 + TypeScript
- **数据库：** SQLite（本地嵌入式数据库）
- **构建工具：** Vite 7.x

### 安全性

- ✅ 所有数据存储在本地
- ✅ 不上传到任何服务器
- ✅ Rust 后端保证内存安全
- ✅ 最小权限原则

### 兼容性

- ✅ Windows 10 (64位) 或更高版本
- ✅ Windows 11 完美支持
- ✅ 支持高DPI显示器

---

## 📖 快速开始

### 绿色版使用

```bash
1. 下载 SitePilot_v0.1.0_Portable.zip
2. 解压到任意位置
3. 双击 SitePilot.exe
4. 开始添加书签！
```

### 安装版使用

```bash
1. 下载 SitePilot_0.1.0_x64-setup.exe
2. 双击运行安装程序
3. 按照向导完成安装
4. 从开始菜单启动
```

### 基本操作

- **添加书签：** 点击右上角 "+" 按钮
- **编辑书签：** 点击书签卡片上的编辑图标
- **删除书签：** 点击书签卡片上的删除图标
- **切换布局：** 点击顶部工具栏的布局按钮
- **切换主题：** 点击顶部工具栏的主题按钮

---

## 💡 使用技巧

### 数据备份

数据存储位置：`%APPDATA%\com.sitepilot.app\`

备份方法：
1. 按 `Win + R` 打开运行
2. 输入 `%APPDATA%\com.sitepilot.app\`
3. 复制整个文件夹到安全位置

### 便携使用

绿色版可以放在U盘中：
- 将解压后的文件夹复制到U盘
- 在任何电脑上都可以运行
- 注意：数据仍会存储在当前电脑的 %APPDATA% 目录

---

## 🐛 已知问题

### 当前版本限制

1. **暂不支持导入/导出**
   - 计划在 v0.2.0 中添加

2. **暂无搜索功能**
   - 计划在 v0.2.0 中添加

3. **暂不支持云同步**
   - 计划在 v0.3.0 中添加

### 已知Bug

目前没有已知的严重Bug。如果您发现任何问题，请[提交Issue](https://github.com/CKEN-STAR/SitePilot/issues)。

---

## 🔄 更新说明

### 如何更新

**绿色版：**
1. 备份数据（`%APPDATA%\com.sitepilot.app\`）
2. 下载新版本
3. 解压覆盖旧版本
4. 数据会自动保留

**安装版：**
1. 下载新版本安装程序
2. 直接安装（会自动覆盖旧版本）
3. 数据会自动保留

---

## 📋 系统要求

### 最低配置

- **操作系统：** Windows 10 (64位)
- **内存：** 2GB RAM
- **磁盘空间：** 100MB
- **网络：** 需要网络连接以获取网站图标

### 推荐配置

- **操作系统：** Windows 11 (64位)
- **内存：** 4GB RAM
- **磁盘空间：** 200MB
- **显示器：** 1920x1080 或更高

---

## 🗺️ 未来规划

### v0.2.0（计划中）

- [ ] 书签导入/导出功能
- [ ] 搜索功能
- [ ] 标签系统
- [ ] 快捷键支持
- [ ] 更多主题

### v0.3.0（计划中）

- [ ] 云同步功能
- [ ] 多语言支持
- [ ] 插件系统
- [ ] 自定义主题编辑器

---

## 🙏 致谢

感谢以下开源项目：

- [Tauri](https://tauri.app/) - 跨平台桌面应用框架
- [React](https://react.dev/) - 用户界面库
- [TypeScript](https://www.typescriptlang.org/) - JavaScript的超集
- [SQLite](https://www.sqlite.org/) - 嵌入式数据库

---

## 📞 支持与反馈

### 问题反馈

如果您遇到任何问题或有功能建议：

- **GitHub Issues：** [提交问题](https://github.com/CKEN-STAR/SitePilot/issues)
- **邮箱：** your-email@example.com

### 文档

- **用户手册：** [README.md](README_RELEASE.md)
- **技术文档：** [TECHNICAL_DOCS.md](TECHNICAL_DOCS.md)
- **部署指南：** [DEPLOYMENT.md](DEPLOYMENT.md)

---

## 📄 许可证

本项目基于 [MIT License](LICENSE) 开源。

---

<div align="center">

**感谢您使用 SitePilot！**

如果觉得有帮助，请给个 ⭐ Star 支持一下！

Made with ❤️ by [CKEN-STAR](https://github.com/CKEN-STAR)

</div>

