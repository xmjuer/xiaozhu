# ☁️ CloudStream: 隐蔽式无限容量离线转存系统

## 简介
这是一个利用 GitHub Actions 算力，配合 Directus 任务队列，将 AList (夸克/PikPak) 中的视频流式切片并转存至 Hugging Face Datasets 的自动化系统。

## 功能特性
*   **支持超大文件**: 采用流式切片 (HLS)，边下边传边删，突破 GitHub 磁盘限制，支持 >15GB 文件。
*   **无限容量**: 依托 Hugging Face Git LFS 存储。
*   **极度隐蔽**: 后端伪装成系统日志，前端伪装成资源管理器。
*   **全平台控制**: 提供适配移动端的 Web 控制台。

## 部署需要的 Secrets
请在 GitHub 仓库 -> Settings -> Secrets -> Actions 中配置：

| Secret Name | 说明 |
| :--- | :--- |
| `DB_CONNECT` | Aiven PostgreSQL 连接字符串 |
| `HF_TOKEN` | Hugging Face Write Token |
| `HF_REPO_ID` | 目标 Dataset ID (例如 `user/repo`) |
| `MAIL_USERNAME` | 发件人邮箱 (QQ邮箱) |
| `MAIL_PASSWORD` | 邮箱 SMTP 授权码 |

## 如何使用
1. 打开部署在 Hugging Face 的前端网页 `index.html`。
2. 填入 AList 域名，连接成功。
3. 勾选文件，点击“转存”。
4. GitHub Actions 会自动运行（每30分钟或手动触发）。
5. 完成后你会收到包含播放链接的邮件。
