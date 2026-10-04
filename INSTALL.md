# 老师端安装与试用

0.2.0 试用版：离线 HTML 只需浏览器；生成新的备课包需要允许运行本地脚本的 Windows PowerShell。生成 PPTX 另外需要微软桌面 PowerPoint。无需上传教师资料或填写 API Token，不会替你购买或激活 Office。老师自己的 WorkBuddy 环境仍需实测。

## 获取

这个仓库是私有的。只有已获授权的 GitHub 账号能访问；登录了自己的账号不等于已有仓库权限。不要把仓库改公开来解决安装问题。

可使用仓库中的 `cv-courseware-starter-0.2.0.zip`，或由项目负责人把同名 ZIP 发给老师。解压到普通本地文件夹，保留 `cv-courseware`、`resources`、`examples` 目录结构。先核对同目录SHA256。`resources` 是精选离线资源，不是老师课件。

不用安装任何技能就能先试看：双击 `examples/euler/student/lesson.html`，断网也能观察模型。拖动模型区域改变观察视角；角度控件与分步按钮控制数学旋转。`examples/euler/teacher` 含通用样例答案，不要发给学生。

使用 Agent 的本地 Skill 导入功能，选择 `cv-courseware` 文件夹。若没有导入界面，先请 Agent 读取其中 `SKILL.md` 再按指令工作。不要猜测某个宿主的安装目录，也不要只复制 `SKILL.md` 而漏掉脚本和参考文件。Codex、WorkBuddy 等不同宿主的导入方式和权限可能不同。

## 给老师 Agent 的第一段话

> 请读取我解压的 cv-courseware/SKILL.md，先使用随附欧拉角示例检查本机能否生成备课包，并打开 examples/euler/student/lesson.html 检查离线三维效果；需要制作PPT时再检查微软桌面PowerPoint。不要安装不明依赖、修改安全设置或上传我的资料。通过后，请使用我提供的下一讲原稿、学生基础和课时，保留教学主线，先制作三页PPT样板。不把欧拉角组件冒充其他学科仿真。检查预览，明确哪些效果已实测；没有资料的地方不要编造。

在私有仓库访问已解决时，可以把开头改为：

> 请读取 https://github.com/2806056580li/teaching-courseware-agent/blob/main/INSTALL.md ，按其中的本地 Skill 安装与试用步骤，帮助我改进下一讲计算机视觉课件。若仓库无权限，请让我提供 ZIP，不要索要密码或 Token。

## 第一次运行

在解压后的 `cv-courseware` 文件夹打开 PowerShell。先阅读脚本；若组织策略阻止脚本运行，交给管理员按单位政策处理，不关闭安全检查或持久改变执行策略。

先生成无需Office的欧拉角备课包，输出目录应当不存在：

```powershell
& .\scripts\Test-LessonPack.ps1 -PackPath .\templates\euler\lesson-pack.json -ResourceDirectory ..\resources
& .\scripts\Build-LessonPack.ps1 -PackPath .\templates\euler\lesson-pack.json -ResourceDirectory ..\resources -OutputDirectory ..\euler-new
```

要同时生成PPT，把第二条改用新的输出目录，并加 `-IncludePowerPoint`。`student/START.txt` 搭配学生学习包一起发，只有 `student` 目录可给学生。教师答案、备课备注留在 `teacher`。

普通课件继续使用原有六种版式生成器：

```powershell
& .\scripts\Test-Environment.ps1
& .\scripts\Test-Lesson.ps1 -LessonPath .\templates\example.json
& .\scripts\Build-Courseware.ps1 -LessonPath .\templates\example.json -OutputPath .\example-output.pptx -PreviewDirectory .\example-preview
```

这是不需下载素材的四页文字/公式示例。包含原生模型的 `demo-3d.json` 随离线包放在包根目录，使用时把上面两处 `LessonPath` 改为 `..\demo-3d.json`，输出改为新的文件名。三维点击姿态会增加物理页数。

资源可直接使用包内 `resources`；联网更新或按章节下载时：

```powershell
& .\scripts\Get-Resources.ps1 -Destination ..\resources -Topics features
& .\scripts\Get-Resources.ps1 -Destination ..\resources -Topics geometry -VerifyOnly
```

不传 `-Topics` 表示整个精选目录，而不是互联网全部资源库。哈希不符、授权/登录弹窗或生成失败时报告具体错误，不把失败当作成功。

## 验收

打开 PPTX 查看全部页面；进入放映，用鼠标点击看模型分步转动并停住。自由拖动三维模型是在编辑视图，首版不提供放映中的自由拖动。先在老师电脑测试，再把三页样板发给老师确认，最后扩展整讲。

Skill 降低版式和原生对象生成难度，不保证不同大模型的学科理解完全相同。数学约定、公式与教学适合度由教师审核。WorkBuddy 实际运行结果需要老师端反馈，不能用开发机测试代替。
