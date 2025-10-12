# SitePilot 发布检查清单

## 📋 发布前检查

### 1. 代码和构建

- [ ] 所有功能正常工作
- [ ] 没有编译错误或警告
- [ ] 已测试所有布局模式
- [ ] 已测试所有主题
- [ ] 已测试计时器功能
- [ ] 已测试书签增删改查
- [ ] 已测试窗口状态记忆

### 2. 版本信息

- [ ] package.json 版本号正确（0.1.0）
- [ ] src-tauri/tauri.conf.json 版本号正确（0.1.0）
- [ ] src-tauri/Cargo.toml 版本号正确（0.1.0）
- [ ] 所有文档中的版本号一致

### 3. 文档准备

- [ ] README_RELEASE.md 已完成
- [ ] TECHNICAL_DOCS.md 已完成
- [ ] RELEASE_NOTES.md 已完成
- [ ] DEPLOYMENT.md 已完成
- [ ] GITHUB_RELEASE_TEMPLATE.md 已完成
- [ ] LICENSE 文件存在
- [ ] 所有文档中的链接有效

### 4. 构建包准备

- [ ] 绿色版已构建（SitePilot_v0.1.0_Portable.zip）
- [ ] NSIS安装程序已构建（SitePilot_0.1.0_x64-setup.exe）
- [ ] MSI安装包已构建（SitePilot_0.1.0_x64_en-US.msi）
- [ ] 所有安装包已测试
- [ ] 计算并记录SHA256校验值

### 5. 测试

#### 绿色版测试
- [ ] 解压后可以正常运行
- [ ] 添加书签功能正常
- [ ] 编辑书签功能正常
- [ ] 删除书签功能正常
- [ ] 图标获取正常
- [ ] 点击打开浏览器正常
- [ ] 布局切换正常
- [ ] 主题切换正常
- [ ] 计时器功能正常
- [ ] 窗口状态记忆正常
- [ ] 关闭后重新打开数据保留

#### 安装版测试
- [ ] 安装程序可以正常运行
- [ ] 安装过程无错误
- [ ] 开始菜单快捷方式创建成功
- [ ] 桌面快捷方式创建成功（如果选择）
- [ ] 程序可以正常启动
- [ ] 所有功能正常
- [ ] 卸载程序正常工作
- [ ] 卸载后数据保留在 %APPDATA%

#### MSI测试
- [ ] MSI安装包可以正常安装
- [ ] 静默安装正常（msiexec /i xxx.msi /quiet）
- [ ] 所有功能正常
- [ ] 静默卸载正常（msiexec /x xxx.msi /quiet）

### 6. 兼容性测试

- [ ] Windows 10 (64位) 测试通过
- [ ] Windows 11 (64位) 测试通过
- [ ] 高DPI显示器测试通过
- [ ] 多显示器测试通过

---

## 🚀 发布流程

### 1. 准备Git仓库

```bash
# 确保所有更改已提交
git status

# 如有未提交的更改，先提交
git add .
git commit -m "Release v0.1.0"

# 推送到远程仓库
git push origin main
```

### 2. 创建Git标签

```bash
# 创建标签
git tag -a v0.1.0 -m "Release v0.1.0"

# 推送标签
git push origin v0.1.0
```

### 3. 计算SHA256校验值

#### Windows PowerShell
```powershell
# 绿色版
Get-FileHash SitePilot_v0.1.0_Portable.zip -Algorithm SHA256

# NSIS安装程序
Get-FileHash src-tauri\target\release\bundle\nsis\SitePilot_0.1.0_x64-setup.exe -Algorithm SHA256

# MSI安装包
Get-FileHash src-tauri\target\release\bundle\msi\SitePilot_0.1.0_x64_en-US.msi -Algorithm SHA256
```

记录校验值：
- [ ] 绿色版 SHA256: `_______________`
- [ ] NSIS SHA256: `_______________`
- [ ] MSI SHA256: `_______________`

### 4. 创建GitHub Release

1. 访问 https://github.com/CKEN-STAR/SitePilot/releases/new

2. 填写信息：
   - Tag: `v0.1.0`
   - Release title: `SitePilot v0.1.0 - 首次发布`
   - Description: 复制 `GITHUB_RELEASE_TEMPLATE.md` 的内容

3. 上传文件：
   - [ ] SitePilot_v0.1.0_Portable.zip
   - [ ] SitePilot_0.1.0_x64-setup.exe
   - [ ] SitePilot_0.1.0_x64_en-US.msi

4. 更新发布说明中的SHA256值

5. 勾选 "Set as the latest release"

6. 点击 "Publish release"

### 5. 更新文档链接

在发布后，更新以下文档中的下载链接：

- [ ] README_RELEASE.md
- [ ] RELEASE_NOTES.md
- [ ] GITHUB_RELEASE_TEMPLATE.md

确保所有链接指向正确的Release页面。

### 6. 验证发布

- [ ] Release页面显示正常
- [ ] 所有下载链接有效
- [ ] 文件可以正常下载
- [ ] 下载的文件可以正常使用

---

## 📢 发布后工作

### 1. 社交媒体宣传（可选）

- [ ] 在Twitter/X上发布
- [ ] 在Reddit相关社区发布
- [ ] 在V2EX发布
- [ ] 在知乎发布

### 2. 收集反馈

- [ ] 监控GitHub Issues
- [ ] 回复用户问题
- [ ] 记录功能建议

### 3. 准备下一版本

- [ ] 创建 v0.2.0 里程碑
- [ ] 规划新功能
- [ ] 整理用户反馈

---

## 📝 发布模板

### GitHub Release 描述模板

```markdown
# 🎉 SitePilot v0.1.0 - 首次发布

> 一款简约而不简单的现代化桌面书签管理器

## 📥 下载

### 🌟 绿色版（推荐）
📦 [SitePilot_v0.1.0_Portable.zip](链接) - 6.93 MB
SHA256: `校验值`

### 📦 安装程序
📦 [SitePilot_0.1.0_x64-setup.exe](链接) - ~20 MB
SHA256: `校验值`

### 🏢 MSI 安装包
📦 [SitePilot_0.1.0_x64_en-US.msi](链接) - ~20 MB
SHA256: `校验值`

## ✨ 主要功能

[复制 GITHUB_RELEASE_TEMPLATE.md 的内容]

## 📖 文档

- [用户手册](README_RELEASE.md)
- [技术文档](TECHNICAL_DOCS.md)
- [发布说明](RELEASE_NOTES.md)

## 🙏 致谢

感谢所有支持者！

---

Made with ❤️ by CKEN-STAR
```

### 社交媒体发布模板

```
🎉 SitePilot v0.1.0 发布了！

一款简约而不简单的现代化桌面书签管理器

✨ 特性：
- 4种华丽的布局模式
- 5种精美主题
- 自动获取网站图标
- 本地存储，保护隐私

📥 下载：https://github.com/CKEN-STAR/SitePilot/releases

#SitePilot #书签管理 #桌面应用 #开源软件
```

---

## ✅ 最终检查

发布前最后确认：

- [ ] 所有测试通过
- [ ] 所有文档完整
- [ ] 所有链接有效
- [ ] 版本号一致
- [ ] Git标签已创建
- [ ] Release已发布
- [ ] 下载链接可用
- [ ] SHA256值正确

---

## 🎊 发布完成！

恭喜！SitePilot v0.1.0 已成功发布！

下一步：
1. 监控用户反馈
2. 修复发现的问题
3. 规划v0.2.0功能

---

**祝发布顺利！** 🚀

