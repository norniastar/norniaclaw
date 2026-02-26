# 本地开发：MySQL + Caddy 代理（草案）

## 你需要提供的参数

- MySQL host/port/user/password/db
- 后端端口（默认示例用 8888）
- 前端端口（默认示例用 5173）

## Caddy

仓库根目录已生成 `Caddyfile`（单入口）：

- `/api/*` → `127.0.0.1:8888`
- 其它 → `127.0.0.1:5173`

启动示例（代理端口为 8090）：

```bash
caddy run --config ./Caddyfile
# 然后访问 http://127.0.0.1:8090
```

## gin-vue-admin 后端 MySQL 配置（本地）

gin-vue-admin 后端支持用环境变量 `GVA_CONFIG` 指定配置文件。

我建议做法（避免泄露密码）：
- 复制 `server/config.local.yaml.example` → `server/config.local.yaml`（该文件已被 `.gitignore` 忽略）
- 用你的本地 MySQL 信息填好
- 启动后端时设置：`GVA_CONFIG=server/config.local.yaml`

我已经在你本机生成了一个 `server/config.local.yaml`（未提交到 git），用于连接你给的本地 MySQL。
