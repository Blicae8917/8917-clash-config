# 8917 Clash Config

一个用于维护和分享 Clash / Mihomo 规则集与配置示例的公开仓库。

## 当前状态

`rules/direct.list` 与 `rules/proxy.list` 已启用，作为 8917 Clash 配置的公开规则正本。两份文件固定导入自已审计的 shiliu 规则快照，后续由 8917 维护；来源和授权边界见 `rules/NOTICE.md`。

`rules/ai.list` 是 8917 自有的 AI 补充规则，用于让 Claude / Anthropic 周边服务与 claude.ai 走同一出口。

## 目录结构

- `rules/direct.list`：确认应直连的公开域名或网段规则。
- `rules/proxy.list`：确认应通过代理的公开域名或网段规则。
- `rules/ai.list`：AI 服务补充规则（Claude / Anthropic 周边域名与桌面进程），交给 AI 策略组。
- `rules/README.md`：规则格式、职责和审阅要求。
- `rules/NOTICE.md`：导入来源、固定提交和授权边界。
- `examples/rule-providers.yaml`：Mihomo `rule-providers` 引用示例。
- `LICENSE`：MIT 许可证。

## Raw 地址

- 直连规则：`https://raw.githubusercontent.com/Blicae8917/8917-clash-config/main/rules/direct.list`
- 代理规则：`https://raw.githubusercontent.com/Blicae8917/8917-clash-config/main/rules/proxy.list`
- AI 补充规则：`https://raw.githubusercontent.com/Blicae8917/8917-clash-config/main/rules/ai.list`

## 安全边界

本公开仓库禁止提交：

- 订阅地址、Token、UUID、密码、私钥和节点凭据；
- 政务网内部 DNS、内部 IP、接口名称和业务拓扑；
- 当前机器可直接运行且含敏感信息的完整 Clash 配置；
- 未确认授权或许可的第三方规则原文。

政务网、UU、Tailscale 和不同机器的本地差异应保留在私有配置或本机覆盖层中，不进入本公开仓库。

## 维护原则

1. 规则按用途拆分，避免把节点、DNS、TUN 和业务分流混在同一个公开文件里。
2. 新增规则必须说明用途，并确认不会泄露内部网络信息。
3. 引入第三方内容前检查来源、更新方式和许可证；优先保留上游链接或生成脚本，而不是无来源复制。
4. 修改后先做 YAML/规则语法检查，再在测试配置中验证命中结果。
5. `rules/direct.list` 与 `rules/proxy.list` 是供配置引用的公开正本；完整 Clash 配置仍只保留在私有工作区。
