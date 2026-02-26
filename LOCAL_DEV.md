# 本地开发：MySQL + Caddy 代理（草案）

## 你需要提供的参数

- MySQL host/port/user/password/db
- 后端端口（默认示例用 8888）
- 前端端口（默认示例用 5173）

## Caddy

仓库根目录已生成 `Caddyfile`（单入口）：

- `/api/*` → `127.0.0.1:8888`
- 其它 → `127.0.0.1:5173`

启动示例：

```bash
caddy run --config ./Caddyfile
```

## gin-vue-admin 后端 MySQL 配置（待你确认）

gin-vue-admin 后端一般读取 `server/config.yaml` / `server/config.docker.yaml`。

我建议做法：
- 不把密码写死进仓库
- 用 `.env`（不提交）或本机环境变量注入，然后在配置里引用/或启动脚本替换

你把 MySQL 连接信息给我，我会把后端改成“默认走本地 MySQL”。
