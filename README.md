# static-resource

用于收集静态资源与常用下载入口。PDF 资料存放在 `pdf/` 目录中。

## GitHub 国内访问加速

以下第三方服务可用于国内网络访问 GitHub 公开资源，不代表服务部署在国内。入口与说明于 **2026-10-28** 查阅；未实测国内网络的下载速度或所有资源类型，可用性以实际访问为准。

| 服务 | 入口 | 用途与说明 |
| --- | --- | --- |
| GHProxy / GHFast | [ghfast.top](https://ghfast.top/) | GitHub 代理加速入口；域名变更可查看[地址发布页](https://ghproxy.link/)。 |
| GHProxy.net | [ghproxy.net](https://ghproxy.net/) | 官网说明支持 Release、源码归档和单个文件，不支持项目文件夹；克隆用法见其首页教程。 |
| GH-Proxy | [gh-proxy.com](https://gh-proxy.com/) | 官网说明支持 Release、Raw、Archive、Gist 和 Git Clone；使用方式见[官方文档](https://gh-proxy.com/docs/github-accelerator)。 |

### 使用方式

通常将完整的原始 HTTPS 链接拼接在代理入口后：

```text
https://加速域名/https://github.com/所有者/仓库/...
```

例如，通过 GH-Proxy 下载 Git 源码归档：

```bash
curl -fL --retry 3 \
    'https://gh-proxy.com/https://github.com/git/git/archive/refs/tags/v2.47.0.tar.gz' \
    -o git-v2.47.0.tar.gz
```

克隆公开仓库：

```bash
git clone https://gh-proxy.com/https://github.com/git/git.git
```

下载 Raw 文件：

```text
https://gh-proxy.com/https://raw.githubusercontent.com/git/git/master/README.md
```

使用时注意：

- 不同服务支持的链接类型和限流策略可能不同；失败时先查看服务说明，再更换入口。
- 仅用于公开资源，不向第三方代理提交 GitHub Token、密码、私有仓库链接或带签名的下载地址。
- 下载可执行文件或安装包后，按上游发布的校验和或签名验证完整性。

## Git 忽略规则

`.gitignore` 覆盖 macOS 的 `.DS_Store`、AppleDouble 等系统文件，以及常见的构建目录、依赖缓存、Python 虚拟环境、日志和本地 `.env` 配置；保留 `.env.example` 等示例配置。

PDF、图片、压缩包和锁文件不做通用忽略，便于正常收集资源和管理依赖版本。若某个资源恰好位于 `build/`、`dist/` 等被忽略的目录，请使用更明确的资源目录名，或按需添加例外规则。
