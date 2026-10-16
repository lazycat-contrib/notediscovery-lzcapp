# NoteDiscovery - LazyCat App

[NoteDiscovery](https://github.com/gamosoft/NoteDiscovery)（自托管 Markdown 知识库）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/gamosoft/notediscovery` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 配置

- 密码保护已启用：部署参数随机 20 位（bcrypt 自动加密），session key 稳定生成
- 数据卷 `/lzcapp/var/notediscovery:/app/data`（Markdown 笔记文件，可直接备份）
- 健康检查 `/health`

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
