# 如何发布 SitePilot 到 GitHub

## 📋 准备工作

### ✅ 已完成的准备

1. **安装包已构建**
   - ✅ 绿色版：`SitePilot_v0.1.0_Portable.zip` (6.93 MB)
   - ✅ NSIS安装程序：`src-tauri\target\release\bundle\nsis\SitePilot_0.1.0_x64-setup.exe` (20.9 MB)
   - ✅ MSI安装包：`src-tauri\target\release\bundle\msi\SitePilot_0.1.0_x64_en-US.msi` (20.5 MB)

2. **SHA256校验值已计算**
   - ✅ 绿色版：`E8B6EBBDBC4F02E4EFEBE07F9E2FC099E347D8A7262C5649F3724C81AD9E471C`
   - ✅ NSIS：`1AB3F1058A6BE739C7E46FE030C22675A2D580C588EE448E0F42EF83ACA32ACA`
   - ✅ MSI：`87C345772AA0E148244772C4089DFF67B03BBE742DF47AABB10D3AC1D5AB1604`

3. **文档已准备**
   - ✅ README_RELEASE.md（用户手册）
   - ✅ TECHNICAL_DOCS.md（技术文档）
   - ✅ RELEASE_NOTES.md（发布说明）
   - ✅ DEPLOYMENT.md（部署指南）
   - ✅ GITHUB_RELEASE_FINAL.md（GitHub Release描述）
   - ✅ LICENSE（MIT许可证）

---

## 🚀 发布步骤

### 步骤1：创建GitHub仓库（如果还没有）

1. 访问 https://github.com/new
2. 填写仓库信息：
   - **Repository name:** `SitePilot`
   - **Description:** `一款简约而不简单的现代化桌面书签管理器`
   - **Visibility:** 选择 `Public`（公开）
   - **不要勾选** "Add a README file"（我们已经有了）
   - **不要勾选** "Add .gitignore"
   - **License:** 选择 `MIT License`
3. 点击 `Create repository`

---

### 步骤2：准备Git仓库

**注意：我们只上传文档，不上传源代码！**

#### 2.1 创建 .gitignore 文件

在项目根目录创建 `.gitignore` 文件，排除源代码：

```gitignore
# 排除所有源代码
src/
src-tauri/
node_modules/
dist/
target/

# 排除构建产物
*.exe
*.msi
*.zip
*.db
*.db-shm
*.db-wal

# 排除配置文件
package.json
package-lock.json
tsconfig.json
vite.config.ts
.vscode/
.idea/

# 排除脚本
create-portable.ps1

# 只保留文档
!README_RELEASE.md
!TECHNICAL_DOCS.md
!RELEASE_NOTES.md
!DEPLOYMENT.md
!GITHUB_RELEASE_FINAL.md
!LICENSE
!.gitignore
```

#### 2.2 初始化Git仓库

```bash
# 初始化Git仓库（如果还没有）
git init

# 添加远程仓库（替换为您的GitHub用户名）
git remote add origin https://github.com/CKEN-STAR/SitePilot.git

# 检查要提交的文件
git status

# 应该只看到文档文件，没有源代码
```

#### 2.3 提交文档

```bash
# 添加文档文件
git add README_RELEASE.md
git add TECHNICAL_DOCS.md
git add RELEASE_NOTES.md
git add DEPLOYMENT.md
git add GITHUB_RELEASE_FINAL.md
git add LICENSE
git add .gitignore

# 提交
git commit -m "Initial release: Documentation for v0.1.0"

# 推送到GitHub
git push -u origin main
```

---

### 步骤3：创建Git标签

```bash
# 创建标签
git tag -a v0.1.0 -m "Release v0.1.0"

# 推送标签
git push origin v0.1.0
```

---

### 步骤4：创建GitHub Release

#### 4.1 访问Release页面

1. 访问您的仓库：`https://github.com/CKEN-STAR/SitePilot`
2. 点击右侧的 `Releases`
3. 点击 `Create a new release`

#### 4.2 填写Release信息

**Choose a tag:**
- 选择 `v0.1.0`（刚才创建的标签）

**Release title:**
```
SitePilot v0.1.0 - 首次发布
```

**Describe this release:**
- 复制 `GITHUB_RELEASE_FINAL.md` 的全部内容
- 粘贴到描述框中

#### 4.3 上传安装包

点击 `Attach binaries by dropping them here or selecting them`

上传以下3个文件：

1. **绿色版：**
   - 文件路径：`D:\Material\Project\SitePilot\SitePilot_v0.1.0_Portable.zip`
   - 上传后重命名为：`SitePilot_v0.1.0_Portable.zip`

2. **NSIS安装程序：**
   - 文件路径：`D:\Material\Project\SitePilot\src-tauri\target\release\bundle\nsis\SitePilot_0.1.0_x64-setup.exe`
   - 上传后重命名为：`SitePilot_0.1.0_x64-setup.exe`

3. **MSI安装包：**
   - 文件路径：`D:\Material\Project\SitePilot\src-tauri\target\release\bundle\msi\SitePilot_0.1.0_x64_en-US.msi`
   - 上传后重命名为：`SitePilot_0.1.0_x64_en-US.msi`

#### 4.4 发布设置

- ✅ 勾选 `Set as the latest release`
- ❌ 不要勾选 `Set as a pre-release`

#### 4.5 发布

点击 `Publish release` 按钮

---

### 步骤5：验证发布

1. 访问 Release 页面，确认：
   - ✅ Release 标题正确
   - ✅ 描述显示正常
   - ✅ 3个安装包都已上传
   - ✅ SHA256值显示正确

2. 测试下载链接：
   - ✅ 点击每个安装包，确认可以下载
   - ✅ 下载后验证SHA256值

3. 检查仓库主页：
   - ✅ README显示正常
   - ✅ 只有文档文件，没有源代码
   - ✅ License显示正确

---

## 📝 发布后工作

### 1. 更新README

在仓库主页添加一个简短的README：

创建 `README.md` 文件：

```markdown
# SitePilot

> 一款简约而不简单的现代化桌面书签管理器

## 📥 下载

前往 [Releases](https://github.com/CKEN-STAR/SitePilot/releases) 页面下载最新版本

## 📖 文档

- [用户手册](README_RELEASE.md)
- [技术文档](TECHNICAL_DOCS.md)
- [发布说明](RELEASE_NOTES.md)

## 📄 许可证

MIT License
```

提交并推送：

```bash
git add README.md
git commit -m "Add README"
git push
```

### 2. 添加仓库描述

在GitHub仓库页面：
1. 点击右上角的 ⚙️ 设置图标
2. 在 `About` 部分：
   - **Description:** `一款简约而不简单的现代化桌面书签管理器`
   - **Website:** 留空或填写您的网站
   - **Topics:** 添加标签：`bookmark-manager`, `desktop-app`, `tauri`, `react`, `windows`
3. 点击 `Save changes`

### 3. 社交媒体宣传（可选）

在以下平台分享您的项目：

**Twitter/X:**
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

**Reddit:**
- r/software
- r/opensource
- r/productivity

**V2EX:**
- 分享创造节点

**知乎:**
- 写一篇详细的介绍文章

---

## ✅ 发布检查清单

发布前最后确认：

- [ ] GitHub仓库已创建
- [ ] .gitignore 已配置（只上传文档）
- [ ] 文档已推送到GitHub
- [ ] Git标签已创建并推送
- [ ] GitHub Release已创建
- [ ] 3个安装包已上传
- [ ] SHA256值已填写
- [ ] 下载链接可用
- [ ] README.md已添加
- [ ] 仓库描述已设置
- [ ] Topics标签已添加

---

## 🎊 完成！

恭喜！SitePilot v0.1.0 已成功发布到GitHub！

**您的项目地址：**
- 仓库：https://github.com/CKEN-STAR/SitePilot
- Release：https://github.com/CKEN-STAR/SitePilot/releases/tag/v0.1.0

**下一步：**
1. 监控GitHub Issues
2. 回复用户问题
3. 收集功能建议
4. 规划v0.2.0

---

**祝发布顺利！** 🚀

