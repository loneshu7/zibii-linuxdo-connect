# zibii-linuxdo-connect

> 子比子主题（Zibii）× Linux DO OAuth 登录集成插件

[![WordPress](https://img.shields.io/badge/WordPress-5.8%2B-blue?logo=wordpress)](https://wordpress.org)
[![PHP](https://img.shields.io/badge/PHP-7.4%2B-purple?logo=php)](https://php.net)
[![License](https://img.shields.io/badge/License-GPL%20v2-green)](LICENSE)

---

## 简介

`zibii-linuxdo-connect` 是一个为 **子比（Zibii）主题** 量身定制的功能扩展插件，通过 **Linux DO** 社区的 OAuth 2.0 接口，让用户可以直接使用 Linux DO 账号登录你的 WordPress 站点。

适合以 Linux DO 社区为目标用户群的个人博客或技术站点使用。

---

## 功能特性

- ✅ 一键通过 Linux DO 账号登录 / 注册
- ✅ 自动同步用户昵称、头像
- ✅ 与子比主题登录弹窗无缝集成
- ✅ 支持绑定已有 WordPress 账号
- ✅ 登录按钮自动注入，无需修改主题模板

---

## 环境要求

| 依赖 | 版本要求 |
|------|----------|
| WordPress | 5.8 + |
| PHP | 7.4 + |
| 子比主题（Zibii） | 最新版 |
| Linux DO OAuth 应用 | 需自行申请 |

---

## 安装方法

### 方式一：直接下载

1. 前往 [Releases](../../releases) 页面下载最新 `.zip` 文件
2. 进入 WordPress 后台 → 插件 → 安装插件 → 上传插件
3. 启用插件

### 方式二：Git 克隆

```bash
cd wp-content/plugins/
git clone https://github.com/your-username/zibii-linuxdo-connect.git
```

然后在 WordPress 后台启用插件。

---

## 配置说明

### 第一步：申请 Linux DO OAuth 应用

1. 前往 [Linux DO 开发者后台](https://connect.linux.do) 创建应用
2. 回调地址填写：`https://你的域名/wp-json/linuxdo/v1/callback`
3. 获取 `Client ID` 和 `Client Secret`

### 第二步：填写插件设置

进入 WordPress 后台 → **设置 → Linux DO 登录**，填入：

```
Client ID:     xxxxxxxxxxxxxxxx
Client Secret: xxxxxxxxxxxxxxxx
```

### 第三步：检查子比主题集成

插件会自动在子比主题的登录弹窗底部注入「Linux DO 登录」按钮，无需额外操作。

如需手动放置按钮，可使用短代码：

```
[linuxdo_login_button]
```

---

## 目录结构

```
zibii-linuxdo-connect/
├── zibii-linuxdo-connect.php   # 插件入口
├── includes/
│   ├── oauth.php               # OAuth 流程处理
│   ├── user.php                # 用户创建 / 绑定逻辑
│   └── hooks.php               # 子比主题钩子注入
├── assets/
│   ├── css/style.css           # 按钮样式
│   └── js/login.js             # 前端交互
├── templates/
│   └── login-button.php        # 登录按钮模板
└── README.md
```

---

## 常见问题

**Q: 登录后头像不显示？**  
A: 请确认子比主题版本为最新，部分旧版本不支持外部头像源。

**Q: 回调地址报 404？**  
A: 进入 WordPress 后台 → 设置 → 固定链接，点一次「保存更改」刷新重写规则。

**Q: 已有账号能绑定 Linux DO 吗？**  
A: 可以。在已登录状态下点击「绑定 Linux DO」即可完成关联。

---

## 贡献

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建你的分支：`git checkout -b feature/xxx`
3. 提交更改：`git commit -m 'feat: 添加 xxx'`
4. 推送分支：`git push origin feature/xxx`
5. 发起 Pull Request

---

## License

本项目基于 [GNU General Public License v2.0](LICENSE) 开源发布，与 WordPress 生态协议保持一致。
