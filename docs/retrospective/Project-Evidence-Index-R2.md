# alw-002-skill 体系地图 · 证据索引 R2（增量）

- 项目根：`<工作区>/alw-002-skill 体系地图`
- 基线：HEAD `6a3139e`（2026-11-09 00:13）＝ `origin/main`，同步 0/0，提交总数 39
- 增量窗口：`0cbad04..HEAD` ＝ 1 个提交（`6a3139e`，+22 / −1，77 → 98 项）
- 上一轮基线：HEAD `0cbad04`，提交总数 38
- 本轮复盘文件：`docs/retrospective/{A-Day1-Reconstruction-R2-V1.0,A-Day1-Reconstruction-R2-V1.1,B-Gap-RootCause-R2-V1.0,B-Gap-RootCause-R2-V1.1,Project-Lessons-R2-V1.0,Project-Evidence-Index-R2}.md`
- 生成时间：2026-11-09

## 一、本轮增量提交

| hash | 时间 | 变化 | 说明 |
|---|---|---|---|
| `6a3139e` | 2026-11-09 00:13 | +22 / −1，77 → 98 | 批量补录积压条目；同批重截三张 PNG |

## 二、条目数阶梯（A 路实测，可逐版复核）

```
125e725 53 → d97f824 57 → 49ce7cb 73 → 63c453a 73 → 32fc5a6 75 → b8ea7b9 76 → 0cbad04 77 → 30772d6 77 → 6a3139e 98
```

- `49ce7cb` 相对 `d97f824` +16：首次批量补漏
- `6a3139e` 相对 `0cbad04` +22 / −1：第二次批量补漏，删除 `main-developer-orchestrator-local-zh`
- 22 条 `updated` 分布：11-02:1、11-03:2、11-04:4、11-05:4、11-06:3、11-07:1、11-08:7，**无一条 11-09** → 连续 7 天累积漏登
- 复现：`git show <rev>:assets/skills.json` 逐版计数

## 三、关键材料与定位

| 材料 | 路径:行 | 证明什么 |
|---|---|---|
| 死引用 11 处 / 8 唯一名 | `index.html:44,45,46,47,52,53,55,56,80,100-102` | 删除条目后写死引用残留；跨 10-31 / 11-03 / 11-09 三轮未清零 |
| 数字算不平 | `index.html:122` | `77+22=98` 类表述无法验算 |
| 领域无条件渲染 | `index.html:80`（`domainOrder` 16 项）、`:100-101`（全量 `map`，不做计数过滤） | 实际 14 个领域，`出行与生活服务`、`需求澄清与决策` 计数为 0 仍显示按钮 |
| 搜索空态 | `index.html:110` | 「没有找到匹配的 Skill」 |
| 加载失败空态 | `index.html:125` | `${err.message}。请稍后刷新页面`；与 `:110` 共用 `td.empty` 样式 |
| 译本陈述三处 | `README.md:29`、`README.en.md:29`、`index.html:61` | 称译本独立展示，而 98 条中 `-trans-zh` 0 条 |
| 页面自述手写 | `index.html:75` | footer 写「页面按登记信息手动更新」 |
| 页面派生处 | `index.html:85`（页脚日期）、`:86-87`（统计卡）、`:113`（热力图总数） | 这三处已由数据派生，不是手写 |
| 过时示意图 | `docs/技能体系示意图.md:3`、`:7` | 「截至 2026-10-29…合计 126 项」；线上 HTTP 200 |
| 全量发布 | `.github/workflows/pages.yml:31` | `path: .` 把整仓发布 |
| 零校验 CI | `.github/workflows/pages.yml` | 仅 checkout → configure → upload → deploy |
| 忽略规则过窄 | `.gitignore`（79 行） | 只忽略 `/local-only/`，未忽略 `docs/retrospective/` |
| 数据文件 | `assets/skills.json` | 98 条、14 个领域、`asOf=2026-11-09` |
| 口径字段不对称 | `assets/iterations.json:4` | `countDefinition` 仅此一处，`skills.json` 无对应字段 |
| 仓库规模 | 全库 12 个文件（html/md/json） | 无 `scripts/`、无 `.sh/.py/.js` |

## 四、线上现取（2026-11-09，A 路 curl 实测）

| 目标 | 结果 |
|---|---|
| `assets/skills.json` | HTTP 200，46,467 B，`len(skills)=98`，`asOf=2026-11-09` |
| `index.html` | 32,290 B，与本地同尺寸 |
| `docs/技能体系示意图.md` | HTTP 200，12,418 B |
| `docs/retrospective/Project-Lessons-V1.0.md` | 404 |

## 五、事实与推断区分

| 结论 | 类型 | 依据 |
|---|---|---|
| 98 项已提交并推送 | 事实 | `HEAD`=`origin/main`=`6a3139e`，工作树仅 `?? docs/retrospective/` |
| 线上 = 98 项 / asOf 11-09 | 事实（curl 现取） | A 路实测，B 路沙箱无网络不可复核 |
| 22 条跨 7 天累积漏登 | 事实 | `updated` 字段逐条分布 |
| 两次批量补漏（+16、+22） | 事实 | 条目数阶梯 |
| 死引用 11 处 / 8 唯一名 | 事实 | `data-skill` 正则提取 29 处 / 26 唯一名，与 98 条求差 |
| `6a3139e` 三张截图同批重截 | 事实 | `git show --stat` 三个 PNG 均为 Bin 变更 |
| 图片度量（2,174×10,092 px、4,090,358 B、`.git` 36 MB） | A 路单向实测 | B 路 Bash 被拒，无独立复核 |
| 「git log --since=2026-10-31 应为 8 条含 d97f824」 | **证据缺口** | 作者日期与提交日期未区分，B 实测为 7 条且不含该提交 |
| 「10-31 地图达 74 项」 | **不成立** | `git show d97f824:assets/skills.json` = 57 |
| 「提交 42 个」 | **不成立** | `git rev-list --count HEAD` = 39 |
| 复盘目录「可能已公开」 | **不成立** | `git ls-files` / `git log --all` 均 0；线上 404 |
| 下一轮系统性复盘仍会漏 | 推断 | 三轮未清零的历史模式 |

## 六、本轮未覆盖

- 未打开浏览器点击页面，零计数域按钮、死引用的实际观感未取证
- 未打开中央登记与 Skill Manager 清单真源，无法反证真源侧是否也有漏登
- 未复核 A 路的 `sips`／`du`／`.git` 体积类度量
- 未验证 README 三张截图缩略后是否真能读到条目数
- 未检查 `temp/`、`docs/` 其他子目录是否因 `path: .` 对外暴露
