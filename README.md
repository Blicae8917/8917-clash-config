# 8917 Clash Config

一个用于维护和分享 Clash / Mihomo 规则集与配置示例的公开仓库。

## 当前状态

仓库已经完成安全骨架初始化。`rules/*.list` 目前只包含注释，没有启用任何真实分流规则；待逐条审阅来源、许可和业务边界后再补充。

## 目录结构

- `rules/direct.list`：确认应直连的公开域名或网段规则。
- `rules/proxy.list`：确认应通过代理的公开域名或网段规则。
- `rules/README.md`：规则格式、职责和审阅要求。
- `examples/rule-providers.yaml`：Mihomo `rule-providers` 引用示例。
- `LICENSE`：MIT 许可证。

## Raw 地址

- 直连规则：`https://raw.githubusercontent.com/Blicae8917/8917-clash-config/main/rules/direct.list`
- 代理规则：`https://raw.githubusercontent.com/Blicae8917/8917-clash-config/main/rules/proxy.list`

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