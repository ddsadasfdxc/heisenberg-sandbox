# heisenberg-sandbox

**毒师宇宙·沙盒** — 基于《绝命毒师》与《风骚律师》的超级自由 MVU 角色卡 + 交互式建号前端。

## 🌐 资源入口

| 资源 | 地址 |
|---|---|
| 🎨 建号前端终端 | https://ddsadasfdxc.github.io/heisenberg-sandbox/onboard.html |
| 🎴 角色卡 JSON | /card/毒师宇宙_沙盒_SAUL-OS_MVU角色卡.json |
| 📚 结构化世界书 | /lorebook/毒师宇宙_沙盒_世界书.json |

## ⚙️ 玩法架构

- **三身份**：穿越者（知晓剧情）/ 原著角色（老白、小粉、索尔、古斯、汉克）/ 原创人物
- **精确时间线**：滑杆选择 1985–2025 任意年份（每一年），自动联动时代主题
- **初始经营**：资金、产品纯度、供应链、初始规模可自设
- **DLC玩法**：洗衣帝国、卡特尔战争、法律攻防、家庭暗线

## 📚 世界书（18条结构化条目）

分类覆盖：核心势力（萨拉曼卡/古斯网络/DEA/街头）、核心人物（沃尔特/杰西/索尔/金/查克等）、地点（阿尔伯克基/奥马哈/墨西哥）、时间线事件（2002/2008/2010）、玩法系统与 MVU 状态协议。

## 🔧 技术实现

1. **外部托管前端**：GitHub Pages 托管精美建号终端（毒师黄黑主题、5步流程、状态合成）
2. **正则注入**：AI 开场白短占位符 `[SAUL-OS] INIT` 被替换为前端 iframe
3. **MVU 变量追踪**：Zod schema 管理资金/纯度/供应链/危险度/法律风险/四势力关系
4. **建号闭环**：前端填表 → 合成用户消息 → 触发 `<initvar>` 初始化

## 🛠️ 构建

卡片由 Node 工程生成：
```
build/modules/01_schema.js   # 变量 Schema + 初始化
build/modules/02_regex_cot.js # 正则规则 + CoT 增量
build/modules/03_identity.js  # 身份/世界观设定
build/modules/04_assemble.js  # 组装 SV3 JSON
build/modules/05_lorebook.js  # 结构化世界书(18条)
```

> 仓库为卡片与前端资源的唯一维护源头，改动后经 GitHub Pages 自动同步生效。


## 🧬 MVU 酒馆助手脚本绑定（v1.1.0）
已参考《剑来》命轨卡标准，绑定 `tavern_helper` 脚本：
- **毒师宇宙·建号配置序列解析**：捕获前端建号消息 → `{{setVar}}` 写入 15 项身份/时间线/资金变量
- **MVU·变量更新引擎**：加载 MagVarUpdate bundle 实现剧情生长式变量持久化
- 30 项变量清单，覆盖 identity/timeline/era/assets/standing/heat/territory/rep/phase/log
- 前端：`https://ddsadasfdxc.github.io/heisenberg-sandbox/onboard.html`（精确年份滑杆 1985–2025）