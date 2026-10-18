# skills of SCI

学术PPT、科研绘图与引用管理技能集合。收录用户指定的三个作者仓库中的六个完整技能目录，保留其脚本、参考资料、资源、许可证和来源。安装日期为 **2026-10-18（Asia/Shanghai）**，具体版本固定到完整 Git commit，见 [UPSTREAMS.md](UPSTREAMS.md)。

## 六个技能

| 技能 | 用途 | 明确调用示例 |
| --- | --- | --- |
| `slides` | 使用 PptxGenJS 创建、编辑可编辑 PowerPoint，渲染和检查溢出、字体 | `$slides 根据我的材料制作一份可编辑的16:9学术PPT，同时交付JS源文件。` |
| `scientific-slides` | 组织研究汇报、学术会议、答辩的叙事、时间和视觉；支持 PPTX、Beamer 或整页图像PDF | `$scientific-slides 为20分钟热振试验报告规划并制作15页学术PPT。` |
| `scientific-visualization` | 科研图表、多面板布局、不确定性、颜色与导出质量检查 | `$scientific-visualization 用我的CSV数据绘制带单位和置信区间的论文图，保留绘图代码。` |
| `citation-management` | 查找论文、核对 DOI/PMID/元数据、生成和整理 BibTeX | `$citation-management 核对这些DOI，合并重复引用并输出BibTeX。` |
| `scientific-schematics` | 经 OpenRouter 生成科学示意图草稿并进行视觉审查；输出位图 | `$scientific-schematics 绘制试验系统流程图；先说明API前提和预计调用，再生成。` |
| `pdf` | 创建、读取、提取和渲染PDF，检查页面布局 | `$pdf 检查这份报告的图表和分页，给出带页码的问题清单。` |

调用示例中的材料和数据需要由当前任务提供。技能能被识别，不代表运行环境、网络、API或具体工作已完成。API服务可能计费，本次未注册、配置或调用付费服务。

## D盘存储与本机Codex发现

实际技能存储在 `D:\.agents\skills\<技能名>`。本仓库的 `skills/` 是版本化副本；当前 Codex 发现链接指向安装目录，而非仓库副本。

本机用户级发现目录是 `%USERPROFILE%\.agents\skills`。六个同名 **Windows Junction** 分别指向 D盘实际技能目录：

```text
%USERPROFILE%\.agents\skills\slides                    -> D:\.agents\skills\slides
%USERPROFILE%\.agents\skills\scientific-slides         -> D:\.agents\skills\scientific-slides
%USERPROFILE%\.agents\skills\scientific-visualization  -> D:\.agents\skills\scientific-visualization
%USERPROFILE%\.agents\skills\citation-management       -> D:\.agents\skills\citation-management
%USERPROFILE%\.agents\skills\scientific-schematics     -> D:\.agents\skills\scientific-schematics
%USERPROFILE%\.agents\skills\pdf                       -> D:\.agents\skills\pdf
```

Codex 官方支持用户级 `.agents/skills` 和链接目录，详见[官方技能文档](https://learn.chatgpt.com/docs/build-skills)。D盘目录不会仅因存在就成为当前C盘项目的用户级扫描目录，因此创建了上述链接。未修改全盘访问权限或Codex安全配置，未替换现有技能。

在本机 Codex `0.162.0-alpha.17.2` 的 `app-server` 上实际调用 `skills/list`、`forceReload:true`：创建链接前六目标为0，创建后六目标全部 `scope:user`、`enabled:true`，无扫描错误。此检查不启动模型对话。当前聊天最初注入的技能清单可能仍是旧快照；下一轮或新聊天再调用，若界面选择器仍未刷新则重启Codex。CLI/IDE可使用 `/skills` 或 `$技能名`，桌面可在技能选择器显式选择；若与内置PDF技能同名，按来源路径选择 `D:\.agents\skills\pdf\SKILL.md`。

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

以上只证明列明探针所覆盖的能力，不表示六个技能所有分支均完成端到端运行。

## 更新技能

1. 仅访问 [UPSTREAMS.md](UPSTREAMS.md) 的作者仓库，核实默认分支、真实路径、许可证及新的完整commit。不要用同名其他来源代替。
2. 使用 Codex 的 `skill-installer`，通过其 `install-skill-from-github.py --repo <作者/仓库> --path <真实目录> --ref <完整commit> --dest <新的暂存父目录>` 下载完整技能；务必使用新的暂存目录，不直接覆盖现有目录。也可从同一固定commit进行git sparse checkout。
3. 按相对路径和文件哈希比较全部原始文件，检查新增/删除的脚本、references、assets和许可证。完全相同则跳过；不同时保留旧版本，明确审批更新范围后再切换目录或链接。本次没有建立自动覆盖更新机制。
4. 更新安装目录后，将六个技能完整复制到本仓库 `skills/`，保留许可证及 `UPSTREAM_SOURCE.json`。更新来源commit、日期、修改说明和校验清单。只提交本任务技能与文档，禁止复制上游 `.git`、密钥和本机个人配置。
5. 重新调用本机 `skills/list` 确认六项被发现，再检查受影响的运行依赖；选择器不刷新则重启Codex。验证后提交并正常推送，不强制推送。

## 来源、许可证与完整性

`slides` 按要求从 JetBrains 仓库取得，其上游元数据中的 OpenAI 作者及原始来源声明已保留；`pdf` 来自 openai/skills。两者保留目录内 Apache-2.0 `LICENSE.txt`。K-Dense四项保留作者仓库 MIT 根许可证的原始副本，位于各技能 `.upstream-licenses/LICENSE.md`。本项目不对不同上游材料统一改许可证。

83个上游原始文件已逐一匹配固定commit的Git blob并核对SHA256。新增内容仅为来源元数据、适用祖先许可证及本仓库中文文档，没有改动技能原始代码和指令。`skills.sha256` 覆盖本仓库技能副本全部文件。

## GitHub仓库

仓库：[BorisW269/skills](https://github.com/BorisW269/skills)。该仓库由用户建立，用户已明确确认以公开方式收录这六个技能；本地工作副本保留在 `D:\skills-of-SCI`。

`skills/` 收录六个完整技能目录，根目录提供中文调用说明、来源commit记录、依赖报告和逐文件SHA256校验清单。仓库保留各上游许可证，不包含凭据、个人资料、其他已安装技能或上游 `.git` 目录。

后续更新先核实上游、比较内容并保留旧版，再通过正常提交更新本仓库；不强制推送、不覆盖无关内容。上传状态和具体commit以GitHub提交历史及本机任务审计记录为准。
