# Changelog

All notable changes to SitePilot will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-10-12

### Added
- 🎉 首次发布

#### 核心功能
- 书签管理系统（添加、编辑、删除）
- 点击书签在默认浏览器中打开
- 自动获取网站Favicon（5个源备用）
- 书签分类管理（10个预设分类 + 自定义分类）

#### 界面布局
- Cards（卡片布局）- 经典网格布局，3D翻转效果
- Carousel（轮播布局）- 横向滚动，波浪流动动画
- Timeline（时间线布局）- 垂直时间线，粒子漂浮效果
- Hexagon（蜂巢布局）- 六边形网格，蜂窝旋转动画

#### 主题系统
- Light（浅色主题）- 清新明亮
- Dark（深色主题）- 优雅深邃
- Blue（蓝色主题）- 科技感
- Purple（紫色主题）- 梦幻感
- Green（绿色主题）- 自然感

#### 计时器功能
- Gradient（渐变光泽）- 紫色渐变 + 光泽扫过
- Neon（霓虹发光）- 黑色背景 + 绿色霓虹
- Glass（玻璃质感）- 毛玻璃效果 + 背景模糊
- Pulse（脉冲跳动）- 红色渐变 + 心跳动画
- Rainbow（彩虹流光）- 彩虹渐变 + 流光动画

#### 动画效果
- 每个布局独特的卡片hover动画
- 每个布局独特的内部背景动画
- 每个布局独特的Favicon背景动画
- 参考Uiverse.io风格，华丽但淡雅

#### 窗口管理
- 使用tauri-plugin-window-state实现窗口状态记忆
- 自动保存窗口大小和位置
- 无闪烁恢复
- 支持自由调整窗口大小

#### 数据持久化
- SQLite本地数据库存储书签
- localStorage保存用户设置（主题、布局、计时器、分类）
- 支持便携式部署

#### 其他功能
- GitHub仓库链接按钮
- 响应式设计
- 加载动画
- 错误提示

### Technical Details
- **框架**: Tauri 2.x
- **前端**: React 18 + TypeScript
- **构建工具**: Vite 7.x
- **数据库**: SQLite (tauri-plugin-sql)
- **样式**: CSS3 (渐变、动画、变换)
- **Tauri插件**:
  - tauri-plugin-sql - 数据库
  - tauri-plugin-opener - 打开浏览器
  - tauri-plugin-http - HTTP请求
  - tauri-plugin-window-state - 窗口状态保存

### Optimizations
- 删除未使用的组件文件
- 删除未使用的依赖（framer-motion）
- 使用CSS3动画替代JavaScript动画库
- 优化Favicon获取策略（多源备用）
- 使用硬件加速的CSS属性（transform, opacity）

### Fixed
- 修复窗口大小记忆闪烁问题
- 修复蜂窝布局边框不明显问题
- 移除GitHub按钮的tooltip

### Known Issues
- 无

### System Requirements
- Windows 10/11
- WebView2运行时（通常已预装）

### Installation
1. 下载.msi或.exe安装程序
2. 双击运行安装
3. 启动SitePilot

### Future Plans
- [ ] 书签搜索功能
- [ ] 书签导入/导出
- [ ] 快捷键支持
- [ ] 书签拖拽排序
- [ ] 更多主题和布局
- [ ] 云同步（可选）
- [ ] 多语言支持
- [ ] 浏览器扩展集成

---

## [Unreleased]

### Planned Features
- 书签搜索和筛选
- 从浏览器导入书签
- 导出书签为JSON/HTML
- 全局快捷键支持
- 书签拖拽排序
- 更多主题选项
- 更多布局模式
- 性能优化（虚拟滚动、图片懒加载）

---

## Version History

- **v1.0.0** - 首次发布（2025-10-12）

---

## Contributors

- CKEN-STAR - 主要开发者

## License

MIT License

## Acknowledgments

- [Tauri](https://tauri.app/) - 跨平台桌面应用框架
- [React](https://react.dev/) - UI框架
- [Uiverse.io](https://uiverse.io/) - 动画设计灵感
- [Google Favicon API](https://www.google.com/s2/favicons) - Favicon服务
- [Favicon.im](https://favicon.im/) - Favicon服务
- [DuckDuckGo Icons](https://icons.duckduckgo.com/) - Favicon服务

---

**Note**: 本项目遵循语义化版本规范。版本号格式为：主版本号.次版本号.修订号
- 主版本号：不兼容的API修改
- 次版本号：向下兼容的功能性新增
- 修订号：向下兼容的问题修正

