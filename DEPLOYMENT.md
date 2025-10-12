# SitePilot 部署指南

## 📦 可用的部署包

SitePilot 提供了3种不同的部署方式，满足不同场景的需求：

### 1. 绿色版（推荐）⭐

**文件：** `SitePilot_v0.1.0_Portable.zip`  
**大小：** 6.93 MB（压缩后）  
**适用场景：** 便携部署、U盘使用、快速测试

**特点：**
- ✅ 解压即用，无需安装
- ✅ 整个文件夹可复制到任何位置
- ✅ 可在任何Windows 10/11电脑运行
- ✅ 删除文件夹即可完全卸载
- ✅ 适合分发给普通用户

**使用方法：**
```
1. 解压 SitePilot_v0.1.0_Portable.zip 到任意位置
2. 双击 SitePilot.exe 启动程序
3. 开始使用！
```

**数据存储：**
- 数据库位置：`%APPDATA%\com.sitepilot.app\sitepilot.db`
- 即使移动程序文件夹，数据仍然保留

---

### 2. NSIS安装程序

**文件：** `src-tauri\target\release\bundle\nsis\SitePilot_0.1.0_x64-setup.exe`  
**适用场景：** 标准安装、普通用户

**特点：**
- ✅ 友好的安装向导
- ✅ 自动创建开始菜单快捷方式
- ✅ 自动创建桌面快捷方式
- ✅ 支持自定义安装路径
- ✅ 提供卸载程序

**使用方法：**
```
1. 双击 SitePilot_0.1.0_x64-setup.exe
2. 按照安装向导完成安装
3. 从开始菜单或桌面启动程序
```

**安装位置：**
- 默认：`C:\Program Files\SitePilot\`
- 数据：`%APPDATA%\com.sitepilot.app\`

---

### 3. MSI安装包

**文件：** `src-tauri\target\release\bundle\msi\SitePilot_0.1.0_x64_en-US.msi`  
**适用场景：** 企业部署、系统管理员

**特点：**
- ✅ 支持组策略部署
- ✅ 支持静默安装
- ✅ 符合企业IT标准
- ✅ 可通过SCCM等工具批量部署

**使用方法：**
```
# 标准安装
双击 SitePilot_0.1.0_x64_en-US.msi

# 静默安装
msiexec /i SitePilot_0.1.0_x64_en-US.msi /quiet

# 静默卸载
msiexec /x SitePilot_0.1.0_x64_en-US.msi /quiet
```

---

## 🔄 重新打包

### 打包所有版本

```bash
# 1. 编译并打包安装程序（MSI + NSIS）
npm run tauri build

# 2. 创建绿色版
powershell -ExecutionPolicy Bypass -File create-portable.ps1
```

### 仅打包绿色版

```bash
# 确保已经编译过
npm run tauri build

# 运行绿色版打包脚本
powershell -ExecutionPolicy Bypass -File create-portable.ps1
```

---

## 📊 部署包对比

| 特性 | 绿色版 | NSIS | MSI |
|------|--------|------|-----|
| 文件大小 | 6.93 MB | ~20 MB | ~20 MB |
| 需要安装 | ❌ | ✅ | ✅ |
| 便携性 | ⭐⭐⭐⭐⭐ | ⭐ | ⭐ |
| 企业部署 | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| 用户友好 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| 快速测试 | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐ |

---

## 🎯 推荐使用场景

### 绿色版适合：
- 👤 个人用户快速使用
- 💾 U盘便携部署
- 🧪 软件测试和演示
- 📤 通过网盘分享
- 🚀 不想安装的用户

### NSIS安装程序适合：
- 👥 普通用户标准安装
- 🏠 家庭用户
- 📱 需要开始菜单快捷方式
- 🎨 需要自定义安装路径

### MSI安装包适合：
- 🏢 企业批量部署
- 👨‍💼 IT管理员
- 🔒 需要组策略控制
- 📋 需要静默安装

---

## 🔐 数字签名（可选）

如果需要对安装程序进行数字签名：

```bash
# 使用 signtool 签名
signtool sign /f certificate.pfx /p password /t http://timestamp.digicert.com SitePilot_0.1.0_x64-setup.exe
```

---

## 📝 发布检查清单

在发布之前，请确认：

- [ ] 所有功能正常工作
- [ ] 已测试所有3种部署方式
- [ ] 版本号正确（package.json, tauri.conf.json）
- [ ] README.md 已更新
- [ ] CHANGELOG.md 已更新
- [ ] LICENSE 文件存在
- [ ] 已创建 GitHub Release
- [ ] 已上传所有安装包
- [ ] 已编写发布说明

---

## 🌐 发布到GitHub

### 1. 创建Release

```bash
# 创建并推送标签
git tag -a v0.1.0 -m "Release v0.1.0"
git push origin v0.1.0
```

### 2. 上传文件

在GitHub Release页面上传以下文件：
- `SitePilot_v0.1.0_Portable.zip` （绿色版）
- `SitePilot_0.1.0_x64-setup.exe` （NSIS安装程序）
- `SitePilot_0.1.0_x64_en-US.msi` （MSI安装包）

### 3. 发布说明模板

```markdown
## SitePilot v0.1.0

### 下载

- **绿色版（推荐）：** [SitePilot_v0.1.0_Portable.zip](链接) - 6.93 MB
- **安装程序：** [SitePilot_0.1.0_x64-setup.exe](链接) - 20 MB
- **MSI安装包：** [SitePilot_0.1.0_x64_en-US.msi](链接) - 20 MB

### 新功能

- ✨ 4种布局模式（Cards、Carousel、Timeline、Hexagon）
- 🎨 5种主题（Light、Dark、Blue、Purple、Green）
- ⏱️ 计时器功能（5种动画样式）
- 💾 窗口状态记忆
- 🏷️ 书签分类管理

### 系统要求

- Windows 10/11 (64位)
- 至少 100MB 可用磁盘空间

### 使用说明

详见 [README.md](链接)
```

---

## 🆘 常见问题

### Q: 绿色版和安装版有什么区别？
A: 功能完全相同，只是部署方式不同。绿色版解压即用，安装版需要安装。

### Q: 数据存储在哪里？
A: 所有版本的数据都存储在 `%APPDATA%\com.sitepilot.app\sitepilot.db`

### Q: 如何备份数据？
A: 复制 `%APPDATA%\com.sitepilot.app\` 文件夹即可。

### Q: 可以同时安装多个版本吗？
A: 不建议。建议卸载旧版本后再安装新版本。

### Q: 绿色版可以在U盘上运行吗？
A: 可以！但数据仍会存储在当前电脑的 %APPDATA% 目录。

---

## 📞 技术支持

- GitHub Issues: https://github.com/CKEN-STAR/SitePilot/issues
- 项目主页: https://github.com/CKEN-STAR/SitePilot

---

**祝您使用愉快！** 🎉

