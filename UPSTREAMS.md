# 上游来源记录

安装日期：2026-10-18（Asia/Shanghai）。所有路径均与用户指定一致，无替代来源或路径迁移。

| 技能 | 作者仓库与目录 | 固定完整commit | 原始文件数 | 本次修改 |
| --- | --- | --- | ---: | --- |
| `slides` | [JetBrains/skills/slides](https://github.com/JetBrains/skills/tree/e0f258b5cfed145015cb3e48da9a97947f7c4ed7/slides) | `e0f258b5cfed145015cb3e48da9a97947f7c4ed7` | 9 | 原始文件未修改；新增来源元数据 |
| `scientific-slides` | [K-Dense-AI/scientific-agent-skills/skills/scientific-slides](https://github.com/K-Dense-AI/scientific-agent-skills/tree/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/scientific-slides) | `a1043ef544e3a100c28e70a736b6cf32554d0677` | 24 | 原始文件未修改；新增来源元数据及MIT祖先许可证 |
| `scientific-visualization` | [K-Dense-AI/scientific-agent-skills/skills/scientific-visualization](https://github.com/K-Dense-AI/scientific-agent-skills/tree/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/scientific-visualization) | `a1043ef544e3a100c28e70a736b6cf32554d0677` | 18 | 原始文件未修改；新增来源元数据及MIT祖先许可证 |
| `citation-management` | [K-Dense-AI/scientific-agent-skills/skills/citation-management](https://github.com/K-Dense-AI/scientific-agent-skills/tree/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/citation-management) | `a1043ef544e3a100c28e70a736b6cf32554d0677` | 22 | 原始文件未修改；新增来源元数据及MIT祖先许可证 |
| `scientific-schematics` | [K-Dense-AI/scientific-agent-skills/skills/scientific-schematics](https://github.com/K-Dense-AI/scientific-agent-skills/tree/a1043ef544e3a100c28e70a736b6cf32554d0677/skills/scientific-schematics) | `a1043ef544e3a100c28e70a736b6cf32554d0677` | 6 | 原始文件未修改；新增来源元数据及MIT祖先许可证 |
| `pdf` | [openai/skills/skills/.curated/pdf](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf) | `49f948faa9258a0c61caceaf225e179651397431` | 4 | 原始文件未修改；新增来源元数据 |

## 许可证与归属

- JetBrains/skills 的 slides：目录内 Apache-2.0 `LICENSE.txt`；保留 `SKILL.md` 中 OpenAI 作者及原始来源声明。
- K-Dense-AI/scientific-agent-skills 的四项技能：作者根 `LICENSE.md`（MIT），原样保存在各技能 `.upstream-licenses/LICENSE.md`。
- openai/skills 的 pdf：目录内 Apache-2.0 `LICENSE.txt`。

## 下载与核验

使用官方 skill-installer 的 GitHub 安装器按完整commit下载完整目录；不嵌入上游 `.git`。83个原始文件均通过对应commit的Git blob核对及安装后SHA256核对。每项 `UPSTREAM_SOURCE.json` 保留来源、真实路径、完整commit、日期及原始文件SHA256。

仅新增来源说明及所需祖先许可证，未修改上游文件。本机暂存路径未写入版本化技能元数据。本地安装目录与本仓库 `skills/` 文件逐项哈希一致。目录完整性清单为 `skills.sha256`。

当前无同名技能冲突；安装、链接与GitHub发布是独立状态。公开收录仓库为 [BorisW269/skills](https://github.com/BorisW269/skills)，经用户明确确认公开上传；实际发布commit见仓库历史。
