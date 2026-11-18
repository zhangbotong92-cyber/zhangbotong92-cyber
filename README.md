# 海桥 / Ocean Relay

写工具的人。偏好**零依赖、能自检、有测试**的实现——不是因为洁癖，是因为我在真实环境里被"一行日志写进 stdout 就让客户端崩掉"这种事坑过。

邮箱：`1024720334@qq.com`

## 在做的东西

### [mcp-bridge](https://github.com/zhangbotong92-cyber/mcp-bridge)

把任意 OpenAI 兼容端点（DeepSeek / Qwen / GLM / Kimi / 本地 ollama）接成 MCP 工具，客户端只配一次。

- 单文件 Python，**只用标准库**，3.8 以上直接跑
- 每次调用落本地 SQLite 账本，可按项目分账——同时伺候几个客户时，月底能说清钱花在哪
- `--doctor` 17 项环境体检；上游不通时回落本机模型，并在回执里明确标注降级
- 7 项协议自检 + 三系统 × 两个 Python 版本的 CI

### [driftguard](https://github.com/zhangbotong92-cyber/driftguard)

自动写配置的工具，怎么判断该不该覆盖用户手改过的文件。

- 三态判断（`ours` / `pristine` / `modified`），只有前两种允许覆盖
- 被跳过时能解释"他改了哪几行"，不是一句"跳过"
- 13 个单元测试，其中最关键那条是"手改后必须内容不变"
- 它解决的是一个**没有报错**的 bug：升级永远不生效，用户以为升了

### [reforge](https://github.com/zhangbotong92-cyber/reforge)

把 AI 生成的图/视频逆向成可复现的配方（prompt + seed + 锁定的 checkpoint），而不是只丢一段提示词。

## 写下来的东西

- [Cursor / Claude Code 在国内用不了模型？按这个顺序查](https://zhangbotong92-cyber.github.io/mcp-bridge/article-02.html)
- [MCP Server 怎么接国内模型](https://zhangbotong92-cyber.github.io/mcp-bridge/article-03.html)
- [MCP 配置生成器](https://zhangbotong92-cyber.github.io/mcp-bridge/config.html)：选客户端与厂商，直接出可粘贴的 JSON
- [把报错发我，免费看一眼](https://zhangbotong92-cyber.github.io/mcp-bridge/diagnose.html)

## 一些做法

- **先复现，再下结论。** 给别人的 issue 回问题，能跑一遍就跑一遍；不能复现的推断，会写明是推断。
- **闸门优先于自觉。** 发布前跑隐私扫描、外链可达性、冒烟测试；写东西有 `ai_smell.py` 量节奏。规矩写在脚本里，不写在口号里。
- **边界写清楚。** 没做到的部分单列一节，不混在"特性"里。

## 许可

上面这些仓库都是 MIT。代码可以随便用，出问题欢迎开 issue。
