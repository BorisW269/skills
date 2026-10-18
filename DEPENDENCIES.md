# 本机依赖检查

检查日期：2026-10-18（Asia/Shanghai）。检查安装于 `D:\.agents\skills` 的六技能原文与脚本。
本报告只表示检查时状态，与技能文件安装、Codex发现、GitHub创建/推送状态分开。
没有安装依赖，没有注册服务或配置API，没有调用付费生成/审阅接口。

## 已实际通过

- 系统 Python 3.9.5：Matplotlib 生成PNG；已安装 scientific-visualization 原生 `style_preview.py` 生成PNG/SVG。
- Codex捆绑 Python 3.12.14：ReportLab生成PDF、pypdf读取验证；已安装 slides 原生 `render_slides.py` 的PDF输入渲染；citation-management 原生BibTeX格式化、去重、重写key；scientific-visualization 原生配色审计。
- 捆绑 Node v24.19.0、PptxGenJS 4.0.1：生成最小PPTX。
- 本机 PowerPoint COM 16.0：隐藏打开最小PPTX，导出PNG和PDF（未要求显示UI）。这是单独验证的PowerPoint通路；上游slides渲染脚本仍需LibreOffice。
- Poppler `pdftoppm`/`pdfinfo` 可调用，PDF渲染退出码0；基础拉丁文本探针出现Symbol/ArialUnicode字体警告。

## Python包实测

系统解释器：`D:\py\Python39\python.exe`。Codex捆绑解释器：`%USERPROFILE%\.cache\codex-runtimes\codex-primary-runtime\dependencies\python\python.exe`。
下表是实际import结果，不能把两个解释器的包当作自动共享；更不能把可import当作整条工作流已验证。

| 依赖 | 系统 Python 3.9.5 | Codex Python 3.12.14 |
|---|---|---|
| numpy | 2.0.2 | 2.3.5 |
| matplotlib | 3.9.4 | 缺失 |
| seaborn | 0.13.2 | 缺失 |
| pandas | 2.3.3 | 3.0.1 |
| scipy | 缺失 | 缺失 |
| pillow | 11.3.0 | 12.3.0 |
| reportlab | 缺失 | 4.4.9 |
| pypdf | 缺失 | 6.10.0 |
| pdfplumber | 缺失 | 0.11.9 |
| pymupdf | 缺失 | 缺失 |
| python-pptx | 缺失 | 1.0.2 |
| pdf2image | 缺失 | 1.17.0 |
| requests | 缺失 | 缺失 |
| bibtexparser | 缺失 | 缺失 |
| scholarly | 缺失 | 缺失 |
| plotly | 缺失 | 缺失 |
| kaleido | 缺失 | 缺失 |
| markitdown | 缺失 | 缺失 |

`bibtexparser` 缺失不阻塞当前citation-management：该版自带标准库BibTeX解析器；`scipy` 也不是六技能所有流程的强制前提。
OpenAI/Google SDK、arxiv/pymed/crossrefapi不是本次上游核心脚本的硬依赖；图像API实际使用requests。

## 每项用途和依赖边界

| 技能 | 用途、所需依赖及当前结果 |
|---|---|
| slides | 可编辑PowerPoint制作、重建、修改、渲染和布局检查。部分就绪：PPT生成与PDF渲染通过；原生PPTX渲染/溢出/字体检查链缺LibreOffice、fontconfig。detect_font.py在Python3.9实际TypeError，需>=3.10。 无必需付费API |
| scientific-slides | 科研报告、会议、答辩的结构、设计、PowerPoint与Beamer制作和审阅。部分就绪：捆绑Python满足版本，Pillow/pypdf/python-pptx和Node/PptxGenJS存在；缺requests、PyMuPDF、LibreOffice、LaTeX、markitdown，当前进程无OpenRouter key。 AI图片生成和视觉review使用OpenRouter，可能计费；未调用 |
| scientific-visualization | 科研图表样式、配色审计、最终尺寸与导出元数据检查。部分就绪：系统Python基础绘图和原生style_preview PNG/SVG通过；捆绑Python无Matplotlib/Seaborn，系统Python无pypdf；Plotly/Kaleido缺失；未复现作者uv+Python3.13固定版本快照。 本地脚本无需付费API |
| citation-management | 文献检索、DOI等元数据获取、BibTeX清理去重与引用检查。部分就绪：format_bibtex.py使用标准库，离线格式化/去重/重写key通过；两Python均缺requests和scholarly。BibTeX解析由自带_common.py实现，不依赖bibtexparser。 NCBI_API_KEY、OPENALEX_API_KEY可选；基础Crossref/PubMed/OpenAlex/arXiv查询按上游设计可无key，仍需网络与服务配额 |
| scientific-schematics | 生成科研PNG示意图草稿，并由视觉模型review及最多两轮生成。未完全就绪：捆绑Python满足版本，缺requests；当前进程未设置OpenRouter key。输出为栅格PNG，无原生矢量/DPI控制。 生成和review均调用OpenRouter，可能计费；未调用 |
| pdf | PDF读取、生成、布局渲染和视觉检查。基础依赖在捆绑Python中就绪；实际PDF生成、pypdf读取、Poppler渲染通过。系统默认Python缺这三个PDF包。Poppler发出Symbol/ArialUnicode字体警告，中文/数学字体需按项目验证。 无必需付费API |

scientific-slides 的独立路径：AI整页/示意图需requests+OpenRouter；图像合并PDF需Pillow；PDF渲染需PyMuPDF；PDF/PPT校验需pypdf/python-pptx；可编辑PPT生成需Node/PptxGenJS；PPT渲染需LibreOffice；Beamer需TeX Live/MiKTeX；模板文本提取可用markitdown。

## 尚缺或兼容风险

- `LibreOffice/soffice` 未发现（PATH、常见安装位置），原生slides PPTX渲染实测报WinError 2；依赖该渲染器的溢出检查也未就绪。`fontconfig` 的fc-list/fc-match未发现，字体审计链未就绪。
- `detect_font.py` 在默认Python 3.9实测因 `ET.Element | None` 注解TypeError；应选>=3.10。scientific-slides上游明确要求>=3.12，scientific-schematics>=3.10；Codex捆绑3.12满足。
- PyMuPDF两解释器均缺失，scientific-slides原生 `pdf_to_images.py` 实测明确报缺PyMuPDF。
- `requests` 两解释器均缺失，影响引用网络检索、引用校验及OpenRouter生成/review；`scholarly` 缺失只影响可选Google Scholar。
- 系统有Matplotlib/Seaborn/Pillow；Codex捆绑有PDF/PPT包，两者未形成一个包齐全的统一环境。scientific-visualization基础样式导出已通过，但作者的uv+Python3.13及固定版本快照未复现；Plotly/Kaleido可选导出也未就绪。
- `pdflatex`/`xelatex`/`lualatex`/`latexmk`/`bibtex`/`biber`、LaTeX常见安装目录未发现；Beamer编译未就绪。
- `markitdown`、`uv`、`npm`、`pdftotext`、ImageMagick `magick`、Graphviz `dot` 未在PATH发现。Windows的`convert.exe`是系统磁盘转换命令，不能当ImageMagick。以上按功能需要选择，均未安装。
- Node模块pptxgenjs、sharp、pdf-lib、playwright可加载；Playwright 1.62.1对应Chromium/Headless Shell缺失，实际launch失败。Playwright并非六项核心流程的统一硬依赖；未下载浏览器。

## API与验证限制

当前进程中 `OPENROUTER_API_KEY`、`OPENAI_API_KEY`、`GEMINI_API_KEY`、`GOOGLE_API_KEY`、`NCBI_API_KEY`、`OPENALEX_API_KEY` 等所查key均未设置。
这里只核对环境变量“存在/不存在”，没有输出任何key，也未遍历个人.env文件；不能据此断言账户从未配置API。
scientific-slides/scientific-schematics的图像生成和视觉review使用OpenRouter，可能计费；本次没有付费API端到端验证。
citation-management的NCBI/OpenAlex key为可选，基础查询仍受外部服务网络、速率和配额限制，本次没有把缺失requests的网络路径声称为已验证。

机器可读原始记录与小型探针仅保留在本机本任务审计目录，不纳入仓库。探针不是正式科研成果。
