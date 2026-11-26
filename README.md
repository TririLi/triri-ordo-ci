# triri-ordo-ci

序 Ordo 的公共 CI 镜像仓（私仓 Actions 被账单拦截，公共仓代跑）。

本仓不含源码：workflow 在运行时通过 `ORDO_SRC_TOKEN` secret 拉取私仓
`TririLi/triri-ordo` 的最新 main，再执行对应门禁。

## 工作流

| 文件 | 内容 | 触发 |
|---|---|---|
| `node-gate.yml` | C1 跨端对账 / C3 生成校验 / 夹具一致性 / 全部 selftest × 双时区 | 手动 / push |
| `android-ci.yml` | Android 模拟器 instrumented 测试（Agent MCP e2e + schema/dao） | 手动 / push |
| `mac-ci.yml` | macOS 前端门禁 + cargo check + universal dmg 构建 | 手动 / push |

手动触发：Actions 页选中 workflow → Run workflow；或 `workflow_dispatch` API。
