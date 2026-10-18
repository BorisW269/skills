# skills of SCI

学术综述、论文写作、英文润色、科研制图、PPT与引用管理技能集合。当前收录12个完整技能目录：此前6项与2026-10-18新增6项；均保留脚本、参考资料、资源、适用许可证和固定来源commit，见 [UPSTREAMS.md](UPSTREAMS.md)。

## 十二个技能

| 技能 | 用途 | 明确调用示例 |
| --- | --- | --- |
| `slides` | 使用 PptxGenJS 创建、编辑可编辑 PowerPoint，渲染和检查溢出、字体 | `$slides 根据我的材料制作一份可编辑的16:9学术PPT，同时交付JS源文件。` |
| `scientific-slides` | 组织研究汇报、学术会议、答辩的叙事、时间和视觉；支持 PPTX、Beamer 或整页图像PDF | `$scientific-slides 为20分钟热振试验报告规划并制作15页学术PPT。` |
| `scientific-visualization` | 科研图表、多面板布局、不确定性、颜色与导出质量检查 | `$scientific-visualization 用我的CSV数据绘制带单位和置信区间的论文图，保留绘图代码。` |
| `citation-management` | 查找论文、核对 DOI/PMID/元数据、生成和整理 BibTeX | `$citation-management 核对这些DOI，合并重复引用并输出BibTeX。` |
| `scientific-schematics` | 经 OpenRouter 生成科学示意图草稿并进行视觉审查；输出位图 | `$scientific-schematics 绘制试验系统流程图；先说明API前提和预计调用，再生成。` |
| `pdf` | 创建、读取、提取和渲染PDF，检查页面布局 | `$pdf 检查这份报告的图表和分页，给出带页码的问题清单。` |
| `literature-review` | 系统、范围及叙述性综述：检索、筛选、提取、主题综合和引用核查 | `$literature-review 围绕热防护结构热振耦合试验制定检索策略，建立证据对比表并组织综述。` |
| `scientific-writing` | 科研论文起草与修订，证据对应、方法结果一致性和全文核对 | `$scientific-writing 根据我的试验数据和已核实文献组织论文，区分观测结果、解释和局限。` |
| `sci-ssci-polishing` | 中文转学术英语和英文润色，保护数字、单位、引用及结论强度 | `$sci-ssci-polishing 润色这段工程论文英文，保持所有数值、术语、引用和结论强度不变。` |
| `venue-templates` | 核实目标期刊当前作者指南，适配结构、写作侧重点和格式 | `$venue-templates 核对目标期刊当前作者指南，并给出本文结构、语言及图表适配清单。` |
| `peer-review` | 投稿前作者自审，检查主张证据、方法、统计、图表及返修回复 | `$peer-review 对这份论文做投稿前自审，按主要问题、次要问题和证据位置输出。` |
| `paper-polisher` | 工程LaTeX论文语言润色，保护公式、TeX、引用键、数值、术语和符号 | `$paper-polisher 润色这个LaTeX项目，保护公式与引用键，并核对术语、符号和数值一致性。` |

调用示例中的材料和数据需要由当前任务提供。技能能被识别，不代表运行环境、网络、API或具体工作已完成。API服务可能计费，本次未注册、配置或调用付费服务。

## D盘存储与本机Codex发现

实际技能存储在 `D:\.agents\skills\<技能名>`。本仓库的 `skills/` 是版本化副本；当前 Codex 发现链接指向安装目录，而非仓库副本。

本机用户级发现目录是 `%USERPROFILE%\.agents\skills`。十二个同名 **Windows Junction** 分别指向 D盘实际技能目录：

```text
%USERPROFILE%\.agents\skills\slides                    -> D:\.agents\skills\slides
%USERPROFILE%\.agents\skills\scientific-slides         -> D:\.agents\skills\scientific-slides
%USERPROFILE%\.agents\skills\scientific-visualization  -> D:\.agents\skills\scientific-visualization
%USERPROFILE%\.agents\skills\citation-management       -> D:\.agents\skills\citation-management
%USERPROFILE%\.agents\skills\scientific-schematics     -> D:\.agents\skills\scientific-schematics
%USERPROFILE%\.agents\skills\pdf                       -> D:\.agents\skills\pdf
%USERPROFILE%\.agents\skills\literature-review -> D:\.agents\skills\literature-review
%USERPROFILE%\.agents\skills\scientific-writing -> D:\.agents\skills\scientific-writing
%USERPROFILE%\.agents\skills\sci-ssci-polishing -> D:\.agents\skills\sci-ssci-polishing
%USERPROFILE%\.agents\skills\venue-templates -> D:\.agents\skills\venue-templates
%USERPROFILE%\.agents\skills\peer-review -> D:\.agents\skills\peer-review
%USERPROFILE%\.agents\skills\paper-polisher -> D:\.agents\skills\paper-polisher
```

Codex 官方支持用户级 `.agents/skills` 和链接目录，详见[官方技能文档](https://learn.chatgpt.com/docs/build-skills)。D盘目录不会仅因存在就成为当前C盘项目的用户级扫描目录，因此创建了上述链接。未修改全盘访问权限或Codex安全配置，未替换现有技能。

此前6项已通过旧版本app-server扫描。本次新增6项的用户级链接与当前Codex实际 `skills/list` 结果见下方“2026-10-18新增技能验证”。技能文件安装、发现列表识别和运行依赖就绪是独立状态；当前聊天的技能快照不等于刷新后的列表。下一轮或新聊天可显式调用，选择器未刷新时重新加载或重启Codex。

## 依赖及验证范围

详见 [DEPENDENCIES.md](DEPENDENCIES.md)。本次仅检查，不自动安装运行依赖，也未调用付费API。

- 系统 `python` 为 **Python 3.9.5**；Codex捆绑 **Python 3.12.14**。二者依赖包不同，不能混用检查结论；`scientific-slides` 要求3.12+，`scientific-visualization` 声明3.11+，`scientific-schematics` 要求3.10+。
- Codex捆绑 **Node.js v24.19.0 / PptxGenJS 4.0.1** 已实际生成PPTX。PptxGenJS位于捆绑模块目录，使用其他Node安装时不保证能直接解析。
- **PowerPoint COM 16.0** 已实际打开探针PPTX并导出PNG和PDF；这是本机可用的渲染通路。上游 `render_slides.py` 的PPTX路径仍依赖 **LibreOffice/soffice**，该项未找到，因此原生PPTX渲染流程仍不完整。
- 基础PDF使用捆绑 `reportlab`、`pypdf` 和 Poppler 已成功生成、读取、渲染；`pdfplumber` 可导入。捆绑Python有这些PDF包和 `python-pptx`；系统Python缺少它们。
- 系统Python已有 Matplotlib/Seaborn，已成功执行科研图表探针和 `style_preview.py`；但其3.9版本低于该技能声明要求，也不匹配上游固定环境。捆绑3.12缺 Matplotlib/Seaborn/SciPy，完整科研绘图环境仍需整理。
- 两个Python环境均缺 **requests**；引用管理的联网检索以及OpenRouter脚本需要它。BibTeX离线格式化探针成功，当前引用技能自带解析逻辑，不强制依赖 `bibtexparser`；`scholarly` 仅Google Scholar路线另需。
- 科学示意图和学术幻灯片的AI图像生成/审查还需 **OPENROUTER_API_KEY** 与网络。本次未配置密钥、验证模型访问或付费额度。`NCBI_API_KEY`、`OPENALEX_API_KEY` 属于引用检索的可选配置。
- **TeX Live/MiKTeX** 的LaTeX命令未找到，Beamer路线未就绪。模板提取使用的 **markitdown** 也未找到。其他可选导出依赖及浏览器组件见详细报告。

以上只证明列明探针所覆盖的能力，不表示所有技能的全部分支均完成端到端运行。

## 更新技能

1. 仅访问 [UPSTREAMS.md](UPSTREAMS.md) 的作者仓库，核实默认分支、真实路径、许可证及新的完整commit。不要用同名其他来源代替。
2. 使用 Codex 的 `skill-installer`，通过其 `install-skill-from-github.py --repo <作者/仓库> --path <真实目录> --ref <完整commit> --dest <新的暂存父目录>` 下载完整技能；务必使用新的暂存目录，不直接覆盖现有目录。也可从同一固定commit进行git sparse checkout。
3. 按相对路径和文件哈希比较全部原始文件，检查新增/删除的脚本、references、assets和许可证。完全相同则跳过；不同时保留旧版本，明确审批更新范围后再切换目录或链接。本次没有建立自动覆盖更新机制。
4. 更新安装目录后，将需要更新的技能完整复制到本仓库 `skills/`，保留许可证及 `UPSTREAM_SOURCE.json`。更新来源commit、日期、修改说明和校验清单。只提交本任务技能与文档，禁止复制上游 `.git`、密钥和本机个人配置。
5. 重新调用本机 `skills/list` 确认预期技能被发现，再检查受影响的运行依赖；选择器不刷新则重启Codex。验证后提交并正常推送，不强制推送。

## 来源、许可证与完整性

`slides` 按要求从 JetBrains 仓库取得，其上游元数据中的 OpenAI 作者及原始来源声明已保留；`pdf` 来自 openai/skills。两者保留目录内 Apache-2.0 `LICENSE.txt`。K-Dense四项保留作者仓库 MIT 根许可证的原始副本，位于各技能 `.upstream-licenses/LICENSE.md`。本项目不对不同上游材料统一改许可证。

此前6项的83个上游原始文件已逐一匹配固定commit的Git blob并核对SHA256；新增6项按安装审计清单逐文件核对，详见追加来源记录。新增内容仅为来源元数据、适用祖先许可证及本仓库中文文档，没有改动技能原始代码和指令。`skills.sha256` 覆盖本仓库技能副本全部文件。

## GitHub仓库

仓库：[BorisW269/skills](https://github.com/BorisW269/skills)。该仓库由用户建立，用户已明确确认以公开方式收录本任务技能；本地工作副本保留在 `D:\skills-of-SCI`。

`skills/` 收录十二个完整技能目录，根目录提供中文调用说明、来源commit记录、依赖报告和逐文件SHA256校验清单。仓库保留各上游许可证，不包含凭据、个人资料、其他已安装技能或上游 `.git` 目录。

后续更新先核实上游、比较内容并保留旧版，再通过正常提交更新本仓库；不强制推送、不覆盖无关内容。上传状态和具体commit以GitHub提交历史及本机任务审计记录为准。

## 2026-10-18新增技能验证

新增 `literature-review`、`scientific-writing`、`sci-ssci-polishing`、`venue-templates`、`peer-review`、`paper-polisher`，此前六项未更新或覆盖。实际安装位置均为 `D:\.agents\skills\<名称>`，本仓库保存完整版本化副本。

语言目标是按具体期刊与研究领域做到准确、简洁、连贯和术语一致。“SCI一区/二区”不是统一文风，也不构成技能可保证的录用结果。推荐顺序：综述检索与证据综合 → 引用核验 → 论文写作 → 期刊适配 → 英文润色 → 图表检查 → 作者自审。LaTeX稿再使用 `paper-polisher` 保护TeX和公式。

新技能的核心指导与本地保真检查不要求额外付费API；联网检索、PDF/LaTeX导出及AI绘图路线存在各自前提。未安装运行依赖、注册付费服务或配置API密钥。依赖检查见 [DEPENDENCIES.md](DEPENDENCIES.md)。本次来源文件均未修改；仅补充来源记录和适用祖先许可证。

本次发现验证使用当前Codex版本 `0.163.0-alpha.10.2`。已在本机调用 `skills/list` 并强制刷新：新增6项均为user作用域且enabled，原6项仍被识别，扫描无错误。下一轮可调用，当前技能选择器如未刷新则重新加载或重启Codex。
