# heisenberg-sandbox

**毒师宇宙·沙盒** — 基于《绝命毒师》与《风骚律师》的超级自由 MVU 角色卡 + 交互式建号前端。

## 🌐 资源入口

| 资源 | 地址 |
|---|---|
| 🎨 建号前端终端 | https://ddsadasfdxc.github.io/heisenberg-sandbox/onboard.html |
| 🎴 角色卡 JSON | /card/毒师宇宙_沙盒_SAUL-OS_MVU角色卡.json |

## ⚙️ 玩法架构

- **三身份**：穿越者（知晓剧情）/ 原著角色（老白、小粉、索尔、古斯、汉克）/ 原创人物
- **多时间线**：2002 / 2008 / 2010后 / 自定义任意年份
- **初始经营**：资金、产品纯度、初始规模可自设
- **DLC玩法**：洗衣帝国、卡特尔战争、法律攻防、家庭暗线

## 🔧 技术实现

1. **外部托管前端**：gitHub Pages 托管 build/onboard.html 精美建号终端（毒师黄黑主题、5步流程、状态合成）
2. **正则注入**：AI 开场白短占位符 `[SAUL-OS] INIT` 被替换为前端 iframe
3. **MVU 变量追踪**：Tom zod schema 管理资金/纯度/供应链/危险度/法律风险/四势力关系/资产/日志
4. **建号闭环**：前端填表 → 合成用户消息 → 触发 `<initvar>` 初始化世界

## 🛠️ 构建

卡片由 Node 工程生成：
```
build/modules/01_schema.js   # 变量 Schema + 初始化
build/modules/02_regex_cot.js # 正则规则 + CoT 增量
build/modules/03_identity.js  # 身份/世界观设定
build/modules/04_assemble.js  # 组装 SV3 JSON
```
运行 `node build/modules/04_assemble.js` 重新生成角色卡。

> 仓库为卡片与前端资源的唯一维护源头，改动后经 GitHub Pages 自动同步生效。
