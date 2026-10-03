# 教师课件增强同类产品调研

核查日期：2026 年 10 月 3 日。

本轮覆盖国内外教师备课工具、通用幻灯片生成工具、Agent 开源项目、分层材料工具和交互三维教学产品。不是对全网所有项目的穷尽调查，也不是付费版实际试用报告。功能依据官方网站、帮助文档和官方 GitHub 仓库；本轮没有安装这些候选项目，没有验证其教学效果或在国内教室网络中的可用性。

## 主要结论

“AI 生成 PPT”“按学习水平改写”“三维教学模型”和“Agent 调用幻灯片生成工具”分别已有同类实现。仅靠这些功能的名称不能认定项目独特。

建议验证的产品定位是：以教师旧课件为主稿，追踪内容变化，按具体知识点匹配经过核验的素材，提供真实交互演示，以及不改变核心知识目标的多层解释。这个组合是否能明显节省备课时间、提高讲解质量，仍需用真实教师试用检验。

## 同类产品

下表“可借鉴之处”是本项目的分析判断，不是厂商承诺。未列出的能力表示本轮未核实，不代表产品没有该能力。

| 项目 | 官方材料确认的功能 | 可借鉴之处与待核实点 |
| --- | --- | --- |
| [MagicSchool](https://www.magicschool.ai/tools/presentation-generator) | 教师用演示文稿生成器；调整主题、图片、布局、语言、内容深度和页数；更新已有课程内容。 | 是“教师课件生成和层次调整”的直接参照。需用真实中文专业课件验证公式、图表与内容保持能力。 |
| [Curipod](https://help.curipod.com/en/articles/739591-can-i-use-my-own-materials-in-a-curipod-lesson) | 可上传 PPT、Keynote、Google Slides 或 PDF，把已有材料变成含理解检查与互动的课程。 | 重点参考旧课件导入和理解检查插入方式，不等同于专业三维模型库。 |
| [Diffit](https://web.diffit.me/diffit-for-differentiation) | 对相同内容提供不同支持方式，调整文本、词汇、题型、难度和认知要求。 | 分层不应只等于把句子变短。[快速入门](https://web.diffit.me/quick-start)还列出了三级难度练习的使用例子；不能把“三级”本身当作独创。 |
| [ClassPoint](https://www.classpoint.io/blog/introducing-classpoint-ai-quiz-generator-in-powerpoint) | 在 PowerPoint 中根据幻灯片生成题目，可选择布鲁姆认知层次，并组织课堂作答。 | 参考教师不离开 PPT 的使用体验；不能由此推断它已有我们的课前选级流程。 |
| [希沃教学大模型](https://www.seewo.com/product/detail/AI) | 基于学科知识库生成教学目标、教学思路和互动课件，支持排版美化，并强调教师可编辑、教学设计由教师主导。 | 国内教学工作流的重要参照。需要区分软件能力、硬件配套和学校部署方案，不能直接照搬全部产品范围。 |
| [Gamma](https://help.gamma.app/en/articles/11047840-how-can-i-import-slides-or-content-into-gamma) | 支持导入文件和演示内容，再进行 AI 辅助处理。 | 可作为旧稿转换与视觉生成的比较对象；导入不等于原版式、动画和公式完全保真。 |
| [SlidesAI](https://help.slidesai.io/generate-from-an-uploaded-document-4m68h) | 从 PDF 或 Word 提取内容生成幻灯片；PowerPoint 工作流可把新幻灯片加入当前文件。 | 参考文档到幻灯片的低门槛入口。未核实与我们要求一致的三级诊断或三维互动能力。 |
| [Presenton](https://github.com/presenton/presenton) | 开源演示生成器，支持文档、设计模板、可编辑 PPTX/PDF、自托管及 API/MCP。 | 是 Agent 入口和生成后端的候选。当前文档说明 Electron 桌面版本不提供 MCP，应区分部署形式。 |
| [PPTAgent](https://github.com/icip-cas/PPTAgent) | 当前开发分支提供供编码 Agent 使用的 Skill，支持创建、修改、视觉审阅和导出可编辑 PPT。 | 与“给 Agent 一段话就制作课件”的入口十分接近；它不是已完成的学科教学资源库。 |
| [Mozaik / mozaWeb 3D](https://us.mozaweb.com/en_US/Product/3dScenes) | 按学科组织交互三维场景，能自由旋转、缩放，并提供标注、特定视图和部分讲解动画。 | 是本项目真正的交互三维教学体验参照。不能把商业平台中的模型直接当作可下载再分发资源。 |

## 开源候选的版本与许可证

- Presenton 仓库根许可证为 [Apache-2.0](https://github.com/presenton/presenton/blob/main/LICENSE)。本轮只阅读，没有下载、部署或集成。代码许可证不替代模型服务、图库和额外素材的各自条款。
- PPTAgent 仓库根许可证为 [MIT](https://github.com/icip-cas/PPTAgent/blob/main/LICENSE)。截至核查日，当前主分支已经转向 Skill 工作流；README 为旧论文运行环境列出固定版本。以后试用必须记录具体版本或提交号，不能混用旧教程与新分支。
- PPTAgent 当前安装要求列出 Linux（含 WSL）或 macOS，以及 uv、npm、LibreOffice 等依赖。不能在未试装前承诺普通 Windows 教师能够直接一键使用。

## 真三维与 PPT 的关系

[Three.js OrbitControls](https://threejs.org/docs/pages/OrbitControls.html) 支持鼠标拖动环绕、缩放和平移。它可以作为互动演示的基础能力；真实模型、教学参数和知识点标注仍需另外设计。

[model-viewer 相机控制示例](https://modelviewer.dev/examples/stagingandcameras/)也展示了通过 camera-controls 为 GLB 模型启用交互的做法。对于需要坐标系、射线、投影面和参数联动的计算机视觉实验，本项目更适合评估 Three.js 场景。

[微软官方 3D 模型说明](https://support.microsoft.com/en-us/office/graphics-visuals/get-creative-with-3d-models)介绍了模型插入、旋转与过渡动画。但“在编辑界面调整视角”“播放预设旋转动画”和“授课放映时现场拖动”不是同一件事。正式承诺前需针对老师使用的 PowerPoint/WPS、版本和放映模式逐一验证。

建议讨论的三条交付路线：

| 路线 | 优点 | 代价与不确定性 |
| --- | --- | --- |
| PPT 配套离线三维演示页 | 保留老师熟悉的 PPT；三维交互独立测试；可准备静态后备图。 | 首版会在 PPT 和演示页之间切换，需要稳定入口与返回流程。 |
| 整体网页课件并导出 PPT | 可把三维、解释层次和内容放在一个授课界面。 | PPT 导出无法默认保留网页交互；老师的编辑习惯会变化。 |
| 原生 PowerPoint 插件或深度嵌入 | 目标是尽量留在 PPT 内授课。 | 安装、Office 版本、平台和 WPS 兼容性增加验证成本，不适合未经原型验证就承诺。 |

当前建议优先讨论第一条路线，不代表已经批准或已经实现。

## 试用时真正要比较什么

1. 原稿内容和公式有没有漏掉、擅自改动或变成不可编辑图片。
2. 老师修改一处内容后，三个解释层和相关图解是否保持一致。
3. 新增的图片或模型是否解释了知识点，而不只是装饰。
4. 交互场景在真实教室电脑上能否流畅加载，断网是否有后备方案。
5. 与老师自己的备课流程、普通大模型和现有 PPT 工具相比，实际节省多少修改时间。
6. 学生能否在讲解后说明概念、读懂图和应用方法，而不只反馈“好看”。

本轮未核实各产品的全部收费套餐、企业集成条款、地域访问条件或教育效果。进入选型阶段后，应以同一份获得授权的样例课件进行对比试用。
