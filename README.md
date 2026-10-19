# Workflow · Aide 工作流能力预设

Aide `workflow` 插件的独立分发仓库，版本 **1.0.0**，MIT 许可。原始源码来自 [Aide f795a240](https://github.com/skyelan1999/aide/tree/f795a240cdb37e9b92a37d91664bd1bb3053b809/plugins/workflow)。

## 能力与边界

| 工具 | 声明用途 | 当前状态 |
| --- | --- | --- |
| `workflow-start` | 启动多阶段工作流 | 仅声明，未提供 handler |
| `workflow-status` | 查询工作流进度 | 仅声明，未提供 handler |

插件还注册 `workflow` 服务名和 `workflow-panel` 面板槽位。当前没有独立的工作流编排、执行或进度存储实现；Aide v1 宿主收集槽位声明，但不渲染通用 UI 槽位。安装此预设不会新增可执行的工作流工具或独立面板。

## 安装

需要支持插件导入的 Aide，市场兼容基线为 `0.1.17.0 RC2`，以及宿主 Node.js 插件运行环境。没有 npm 依赖。

从 [Release](https://github.com/skyelan1999/aide-pkg-workflow/releases/tag/v1.0.0) 说明中的固定提交链接下载 `aide-pkg-workflow-v1.0.0.zip` 和 `SHA256SUMS`，核对摘要后通过 Aide 插件管理导入；也可在[官方插件市场](https://skyelan1999.github.io/aide-pkg-shop/)搜索 `workflow`。

```sh
sha256sum -c SHA256SUMS
```

安装 ZIP 与既有市场 1.0.0 包逐字节一致，根目录包含 `index.js`、`manifest.json`、`LICENSE`。保留原版本和运行行为；已有同 ID、同版本的插件无需重复安装。

## 分发与验证

安装 ZIP 与摘要由本仓库的 `packages/v1.0.0/` 目录托管，Release 说明提供固定提交的下载链接；它们不是额外上传的 Release 附件。市场分发相同字节的安装包。

发布前检查 Node 语法、ZIP 完整性与 SHA-256，并使用 Aide 宿主校验入口和加载 surface，确认两个工具均不可执行。成功加载不等于工作流执行功能验收通过。

此预设自身不读取文件、不执行命令、不连接网络。Node 插件机制不是权限沙箱；SHA-256 用于完整性校验，不是发布者签名。
