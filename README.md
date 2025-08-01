# 🌸 米游社自动签到助手

> ✅ 基于 [MihoyoBBSTools](https://github.com/Womsxd/MihoyoBBSTools) 的增强版，支持 **GitHub Actions 全自动签到**  
> 🕒 每日凌晨自动执行，无需服务器，零成本挂机

---

## 🚀 快速开始（GitHub Actions 部署）

### ① 克隆原始仓库
1. 打开 [GitHub 仓库导入页面](https://github.com/new/import)
2. 填写以下信息：
   - **Source repository URL**：`https://github.com/Womsxd/MihoyoBBSTools`
   - **Repository name**：`MihoyoBBSTools`（可自定义）
   - **Private**：✅ 建议勾选（保护隐私）
3. 点击 **Begin import** 开始导入

---

### ② 上传增强文件
将本仓库的以下文件上传到新仓库对应位置：

| 文件 | 上传路径 | 说明 |
|---|---|---|
| `main.py` | `/` | 替换原签到脚本 |
| `Checkin.yml` | `/.github/workflows/` | 自动签到工作流 |
| `keep_alive.yml` | `/.github/workflows/` | 防休眠工作流 |
| `config.yaml` | `/config/` | 配置文件 |

---

### ③ 配置 Cookie 和 SToken
#### 🔑 添加 Cookie
1. 进入仓库 → `Settings` → `Secrets and variables` → `Actions`
2. 点击 **New repository secret**：
   - **Name**：`COOKIE`
   - **Value**：粘贴完整 Cookie（示例格式）：
     ```
     mid=xxx;stoken=v2_xxx=.CAE=;stuid=xxx;ltoken=xxx;ltuid=xxx;account_id=xxx;cookie_token=xxx
     ```

#### 🔐 添加 SToken
- **Name**：`STOKEN`
- **Value**：`v2_xxx=`（仅 `stoken` 值）

---

## ✅ 测试运行
1. 进入仓库 → `Actions` → `Checkin` → `Run workflow` → 点击 **Run workflow**
2. 观察日志：
   - 成功日志示例：`✅ 签到成功`
   - 失败日志会提示错误原因（如 Cookie 失效）

---

## ⏰ 定时说明
- **默认时间**：每日 **00:13 (北京时间)** 自动运行
- **修改方法**：编辑 `.github/workflows/Checkin.yml` 中的：
  ```yaml
  - cron: '13 16 * * *'  # UTC时间，北京时间+8