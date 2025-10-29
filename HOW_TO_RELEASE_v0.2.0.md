# 📦 SitePilot v0.2.0 发布指南

> **手把手教你发布到GitHub - 每一步都详细说明**

---

## 📋 准备工作检查清单

### ✅ 已完成的准备

1. **安装包已构建**
   - ✅ NSIS安装程序：`src-tauri\target\release\bundle\nsis\SitePilot_0.2.0_x64-setup.exe` (44 MB)
   - ✅ MSI安装包：`src-tauri\target\release\bundle\msi\SitePilot_0.2.0_x64_en-US.msi` (95 MB)
   - ✅ 绿色版：`src-tauri\target\release\bundle\portable\SitePilot_0.2.0_x64_portable.exe` (103 MB)

2. **文档已准备**
   - ✅ GITHUB_RELEASE_v0.2.0.md（GitHub Release描述）
   - ✅ CHANGELOG.md（更新日志）
   - ✅ LICENSE（MIT许可证）

---

## 🚀 发布步骤（手把手教学）

### 步骤1：创建绿色版压缩包

#### 1.1 打开PowerShell

1. 按 `Win + X` 键
2. 选择 "Windows PowerShell" 或 "终端"
3. 输入以下命令切换到项目目录：

```powershell
cd D:\Material\Project\SitePilot
```

#### 1.2 创建绿色版文件夹

```powershell
# 创建临时文件夹
New-Item -ItemType Directory -Force -Path "SitePilot-Portable-v0.2.0"

# 复制可执行文件
Copy-Item "src-tauri\target\release\bundle\portable\SitePilot_0.2.0_x64_portable.exe" "SitePilot-Portable-v0.2.0\SitePilot.exe"

# 创建README文件
@"
# SitePilot v0.2.0 绿色便携版

## 使用方法

1. 双击 SitePilot.exe 启动程序
2. 点击右上角 "+" 添加书签
3. 尽情使用！

## 数据存储位置

%APPDATA%\com.sitepilot.app\

## 备份数据

1. 按 Win + R
2. 输入：%APPDATA%\com.sitepilot.app\
3. 复制整个文件夹到安全位置

## 版本信息

- 版本：v0.2.0
- 发布日期：2025-01-29
- 许可证：MIT License

## 更多信息

https://github.com/CKEN-STAR/SitePilot
"@ | Out-File -FilePath "SitePilot-Portable-v0.2.0\README.txt" -Encoding UTF8

# 复制许可证
Copy-Item "LICENSE" "SitePilot-Portable-v0.2.0\LICENSE.txt"
```

#### 1.3 压缩文件夹

```powershell
# 压缩为ZIP文件
Compress-Archive -Path "SitePilot-Portable-v0.2.0\*" -DestinationPath "SitePilot_v0.2.0_Portable.zip" -Force

# 删除临时文件夹
Remove-Item -Path "SitePilot-Portable-v0.2.0" -Recurse -Force
```

---

### 步骤2：计算SHA256校验值

```powershell
# 计算绿色版SHA256
Get-FileHash "SitePilot_v0.2.0_Portable.zip" -Algorithm SHA256 | Select-Object Hash

# 计算NSIS安装程序SHA256
Get-FileHash "src-tauri\target\release\bundle\nsis\SitePilot_0.2.0_x64-setup.exe" -Algorithm SHA256 | Select-Object Hash

# 计算MSI安装包SHA256
Get-FileHash "src-tauri\target\release\bundle\msi\SitePilot_0.2.0_x64_en-US.msi" -Algorithm SHA256 | Select-Object Hash
```

**记录这三个SHA256值，稍后需要填写到GitHub Release中！**

示例输出：
```
Hash
----
ABCD1234EFGH5678...（64位十六进制字符串）
```

**请将这三个SHA256值复制到记事本中保存！**

---

### 步骤3：准备Git仓库

#### 3.1 检查Git状态

```powershell
# 查看当前状态
git status
```

#### 3.2 提交所有更改

```powershell
# 添加所有更改
git add .

# 提交更改
git commit -m "Release v0.2.0: 新增5种布局、5种主题、自定义主题编辑器、浏览器选择等功能"

# 推送到GitHub
git push origin main
```

**如果提示需要登录GitHub，请按照提示操作。**

---

### 步骤4：创建Git标签

```powershell
# 创建标签
git tag -a v0.2.0 -m "Release v0.2.0"

# 推送标签到GitHub
git push origin v0.2.0
```

**成功后会显示：**
```
To https://github.com/CKEN-STAR/SitePilot.git
 * [new tag]         v0.2.0 -> v0.2.0
```

---

### 步骤5：创建GitHub Release（详细步骤）

#### 5.1 打开浏览器

1. 打开您的浏览器（Chrome、Edge等）
2. 在地址栏输入：`https://github.com/CKEN-STAR/SitePilot`
3. 按回车键

#### 5.2 进入Releases页面

1. 在仓库页面，找到右侧的 **"Releases"** 链接
2. 点击 **"Releases"**
3. 点击 **"Create a new release"** 按钮（绿色按钮）

**或者直接访问：**
```
https://github.com/CKEN-STAR/SitePilot/releases/new
```

#### 5.3 填写Release信息

**Choose a tag（选择标签）：**
1. 点击下拉框
2. 选择 `v0.2.0`（刚才创建的标签）

**Release title（发布标题）：**
```
SitePilot v0.2.0 - 重大更新
```

**Describe this release（描述此版本）：**

1. 打开文件：`D:\Material\Project\SitePilot\GITHUB_RELEASE_v0.2.0.md`
2. 按 `Ctrl + A` 全选内容
3. 按 `Ctrl + C` 复制
4. 回到GitHub页面
5. 在描述框中按 `Ctrl + V` 粘贴

**重要：更新SHA256值！**

在粘贴的内容中，找到以下三处：

```markdown
**SHA256:** `待计算`
```

将 `待计算` 替换为您在步骤2中记录的实际SHA256值。

#### 5.4 上传安装包

1. 向下滚动到 **"Attach binaries"** 部分
2. 点击 **"Attach binaries by dropping them here or selecting them"**

**上传以下3个文件：**

**文件1：绿色版**
- 文件路径：`D:\Material\Project\SitePilot\SitePilot_v0.2.0_Portable.zip`
- 拖拽或选择此文件上传

**文件2：NSIS安装程序**
- 文件路径：`D:\Material\Project\SitePilot\src-tauri\target\release\bundle\nsis\SitePilot_0.2.0_x64-setup.exe`
- 拖拽或选择此文件上传

**文件3：MSI安装包**
- 文件路径：`D:\Material\Project\SitePilot\src-tauri\target\release\bundle\msi\SitePilot_0.2.0_x64_en-US.msi`
- 拖拽或选择此文件上传

**等待上传完成！** 每个文件上传后会显示绿色的勾号 ✅

#### 5.5 发布设置

1. **勾选** ✅ `Set as the latest release`（设置为最新版本）
2. **不要勾选** ❌ `Set as a pre-release`（不是预发布版本）

#### 5.6 发布！

1. 检查所有信息是否正确
2. 点击绿色的 **"Publish release"** 按钮
3. 等待几秒钟...
4. 🎉 发布成功！

---

### 步骤6：验证发布

#### 6.1 检查Release页面

1. 访问：`https://github.com/CKEN-STAR/SitePilot/releases`
2. 确认看到 `v0.2.0` 版本
3. 确认标题为 "SitePilot v0.2.0 - 重大更新"
4. 确认描述显示正常
5. 确认3个安装包都已上传

#### 6.2 测试下载链接

1. 点击每个安装包的下载链接
2. 确认可以正常下载
3. 下载后验证文件大小是否正确：
   - 绿色版：约 7-10 MB（压缩后）
   - NSIS：44 MB
   - MSI：95 MB

#### 6.3 验证SHA256（可选）

```powershell
# 下载后验证SHA256
Get-FileHash "下载的文件路径" -Algorithm SHA256
```

对比是否与Release页面显示的一致。

---

## 📝 发布后工作

### 1. 更新README（可选）

如果您想在仓库主页添加一个简短的README：

```powershell
# 创建README.md
@"
# SitePilot

> 一款简约而不简单的现代化桌面书签管理器

## 📥 下载最新版本

前往 [Releases](https://github.com/CKEN-STAR/SitePilot/releases) 页面下载 v0.2.0

## ✨ v0.2.0 新功能

- 🎨 新增5种布局模式（瀑布流、网格、3D立方体、杂志、看板）
- 🌈 新增5种主题（日落、海洋、森林、赛博朋克、极简）
- 🎨 自定义主题编辑器
- ⏱️ 增强计时器（正计时/倒计时）
- 🌐 浏览器检测和选择
- 📝 查看备注功能
- 🎬 增强动画效果

## 📖 文档

- [更新日志](CHANGELOG.md)
- [许可证](LICENSE)

## 📄 许可证

MIT License
"@ | Out-File -FilePath "README.md" -Encoding UTF8

# 提交README
git add README.md
git commit -m "Add README for v0.2.0"
git push
```

### 2. 添加仓库描述

1. 访问：`https://github.com/CKEN-STAR/SitePilot`
2. 点击右上角的 ⚙️ **Settings** 图标（在About部分）
3. 填写：
   - **Description:** `一款简约而不简单的现代化桌面书签管理器`
   - **Website:** 留空
   - **Topics:** 添加标签：
     - `bookmark-manager`
     - `desktop-app`
     - `tauri`
     - `react`
     - `windows`
     - `typescript`
4. 点击 **"Save changes"**

---

## ✅ 发布检查清单

发布前最后确认：

- [ ] 绿色版ZIP已创建
- [ ] SHA256值已计算并记录
- [ ] Git更改已提交并推送
- [ ] Git标签v0.2.0已创建并推送
- [ ] GitHub Release已创建
- [ ] Release标题正确
- [ ] Release描述已粘贴
- [ ] SHA256值已更新到描述中
- [ ] 3个安装包已上传
- [ ] "Set as the latest release"已勾选
- [ ] Release已发布
- [ ] 下载链接可用
- [ ] README.md已更新（可选）
- [ ] 仓库描述已设置（可选）

---

## 🎊 完成！

恭喜！SitePilot v0.2.0 已成功发布到GitHub！

**您的项目地址：**
- 仓库：https://github.com/CKEN-STAR/SitePilot
- Release：https://github.com/CKEN-STAR/SitePilot/releases/tag/v0.2.0

**下一步：**
1. 监控GitHub Issues
2. 回复用户问题
3. 收集功能建议
4. 规划v0.3.0

---

**祝发布顺利！** 🚀

