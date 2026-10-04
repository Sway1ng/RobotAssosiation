# zju机协会教学部纳新材料

本项目包含一份内训课程设计和一套授课型幻灯片，面向具有基础 C 语言知识、缺少电子与嵌入式开发经验的同学。

## 问题回答与简介
- 1. 你在本次任务中使用了哪些 Git 或 GitHub 功能？
- 2. 操作过程中遇到了哪些问题？你是如何解决的？
- 3. 如果将来需要多名教学部成员共同维护这个仓库，你认为应当如何组织文件与修改流程？
- 4. 本次纳新题中是否使用了 AI 工具？如果使用，请说明 AI 参与了哪些部分，以及你进行了哪些检查与修改。

1. 对纳新题对所有项目使用git进行版本管理和维护，使用了add, commit, remote及其相关命令, push...
2. github网络连接问题（原来的加速器最近多有波动）！换加速器改host。其余多为命令使用不熟练导致的，上网翻阅教程即可快速解决。
3. 小修正直接提交；新增章节、调整教学目标或更换硬件，在独立分支修改，并提交 Pull Request：写清修改内容、验证方式。并由另一名成员审核合并后发布。
   
参考目录格式（由AI生成）：

```text
RobotAssosiation/
├── README.md                  # 课程索引、预览方式与维护入口
├── CONTRIBUTING.md            # 修改、审核与发布规范
├── courses/
│   └── pwm-motor-control/
│       ├── README.md          # 课程对象、基础、课时、设备与负责人
│       ├── lesson-plan.md     # 教案与课时安排
│       ├── slides.md          # Marp 幻灯片源文件
│       ├── assets/
│       │   └── SOURCES.md     # 图片来源、许可与修改记录
│       └── examples/          # 可运行的 Arduino 示例
├── shared/
│   ├── themes/                # 公共 Marp 样式
│   └── templates/             # 教案与幻灯片模板
└── scripts/                   # 统一导出与检查脚本
```

4.本次纳新题全程使用AI工具（codex接GPT-6sol,6.1sol,Astra），具体使用细节在纳新题总文件的README中有详细介绍，主要在附加题三中进行了vibe-coding多次迭代。AI生成信息核查为项目完成后指示AI自审查+本人审阅后提出改进意见。

现在主要对教学部教案设计进行介绍说明：课题的选题由gpt提供多种参考方向，由我敲定后再由其生成几个具体项目供我参考，最终拟定以STM32驱动小车为最终选题。

在网上寻找相关教程，我拟定了课程的基本框架与内容，并由gpt提供初版授课方案。课程总共分为四节，主要目的是让会员能在技术实践中理解并掌握单片机开发的基本流程。受制于本人自身的实践经历，内容较为基础，皆为自己之前尝试过的内容，也因此比较容易上手。AI设计的教学计划较为合理，我只做了适当的简化筛选，并加入补充了部分我觉得较为重要的内容（如后面pwm教学中的控制论内容）。

授课demo主要围绕教案的第二课时展开，以电路部分为灵感，选择了UNO和L298N为平台，降低使用门槛。主要讲解了PWM技术的基本原理，呼吸灯和电机变速这些经典案例，并拓展了开闭环控制基础，为后面循迹小车可能用到的PID控制理论打下基础。

后面的介绍皆为AI生成，可供阅读参考。

## 材料介绍

**课程设计：STM32 实时控制入门——从点灯到智能小车。** 以基础循迹小车为最终项目，共 4 次课、约 9 小时，从基本元件、供电与接线出发，逐步学习 GPIO、PWM、串口和红外循迹，最后完成系统调试与展示。

**授课 Demo：PWM 与电机控制。** 以 Arduino UNO R3 和 L298N 为演示硬件，讲解占空比、定时器、呼吸灯、非阻塞调度、电机驱动和开闭环控制。Arduino 示例用于降低演示门槛，整体内训方案仍以 STM32 为平台。

当前幻灯片共 19 页，完整讲解会超过纳新要求的约 10 分钟。演示时建议围绕“PWM 概念 → Arduino 实现 → 电机接线与控制 → 输出反馈”选择重点页面，其他页面用于补充阅读或答疑。

## 目录

- `slides/`：PWM 与电机控制授课型幻灯片、Markdown 源文件、HTML 预览及图片资源。
- `topic/`：STM32 实时控制入门课程设计及 HTML 预览。

## 预览

直接用浏览器打开 [PWM-demo.html](slides/PWM-demo.html)，使用左右方向键翻页，无需安装 Marp。

推荐先阅读 [课程设计](topic/STM32实时控制入门课程设计.md)，再查看幻灯片。`slides/` 内的早期大纲仅供教学结构参考，实际内容以最终 Markdown 源文件和 HTML 为准。

Markdown 与 HTML 中的图片使用同目录下的 `assets/` 相对路径。移动或提交材料时请保留整个 `slides/` 目录。

## 编辑与导出

幻灯片使用 Markdown + [Marp](https://marp.app/) 制作。安装 Node.js 和 Marp CLI 后，在项目根目录运行：

```bash
npm install -g @marp-team/marp-cli
marp "slides/PWM与电机控制授课型幻灯片Demo.md" --html --allow-local-files --output "slides/PWM-demo.html"
```

也可以使用 VS Code 的 Marp for VS Code 扩展编辑与预览。源文件包含 HTML 布局，需启用 HTML 支持。修改 Markdown 后重新导出 HTML，并检查代码与图片排版。波形动画在 HTML 中播放，静态导出保留静态效果。

## 说明

示例使用 Arduino UNO R3、L298N、直流电机、LED 与限流电阻、按键及外部电机电源。单电机程序采用 D5 → ENA、D7 → IN1、D8 → IN2；按键接 D2 与 GND。

硬件图片来自 [Last Minute Engineers 的 L298N 教程](https://lastminuteengineers.com/l298n-dc-stepper-driver-arduino-tutorial/)，课件保留了来源标注。图中双电机示例与本课单电机程序的引脚不同，搭建时按课件中的对应表连接。共地、逻辑供电与跳线帽设置见接线页面。

PWM 理论参考 Arduino 的 [analogWrite 文档](https://docs.arduino.cc/language-reference/en/functions/analog-io/analogWrite/)及 [Secrets of Arduino PWM](https://docs.arduino.cc/tutorials/generic/secrets-of-arduino-pwm/)。课件中的默认频率、定时器和引脚分配针对 UNO R3 AVR 平台，其他开发板应查对应文档。
