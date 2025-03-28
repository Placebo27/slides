会议主题：引导程序中的大模型产品

时间：2025年2月17日

地点：在线

参会人员：[xingyuma618 · GitHub](https://github.com/xingyuma618);[luojia65 (Luo Jia / Zhouqi Jiang) · GitHub](https://github.com/luojia65)

议程：

经过会议讨论，我们认为带🌟的项目是适合近期实际开展的。

- 自组织和自修复引导程序

1. 用自然语言描述需求，从各个组件生成引导程序软件，自动生成引导程序代码。

   编写胶水代码：RAG项目。大模型没有使用最新语料训练，需要使用RAG知识库。模块的代码收到token数量的限制。大模型可以通过函数的描述（函数名、参数等）写程序，缩短代码量。大模型需要详细的注释，简单的注释反而是噪声；太复杂的注释会让token量增加。

2. 启动过程故障（以及kernel panic）时，借助大模型能力和引导程序应用接口，自动化地解释甚至修复故障

   存在自动程序修复这个研究方向。大模型可以做代码修复，缺点是：不常见的代码，大模型没有训练过相应数据（训练语料少），它的修复能力会不好。需要根据引导程序是否常见，来确定。若项目的规模较小，训练预料较少，大模型修复的效果不一定好。可以认为加入对算法的描述、代码撰写的经验（经常出现怎样的错误等）或简单的数据集作为输入文本（人类专家补充样例或经验性的描述）。

   修复内核代码考虑代码行数庞大。例如，满血DeepSeek只能处理10万token，约十几万字符。分析模块，需要考虑模块与其它模块的关联性，没有上下文，效果变差。字符越多，效果越差（超过10万字符效果较差）。

   (🌟是一个学术项目，不一定能短期在工业界找到应用)

- 自然语言用户接口

1. 用自然语言作为命令行的补充与用户交互，降低引导过程的调试门槛。

   不容易实现。大模型只能输入和输出文本。大模型没有感知能力，需要接入外部的调试服务完成对设备故障的感知能力。

   大模型做复杂运算时容易出错，最靠谱的做法是生成一段代码，运行代码完成输出。

2. 按需生成图形化界面大模型

   大模型可以生成前端代码，可以生成常用的前端功能。

- 系统软件开发辅助工具

1. 具有专业知识库的大模型智能体可以聊天机器人的形式，辅助裸机系统软件开发者，以提高工作效率。

   （🌟也就是今天的RustSBI Agent项目）

2. 大模型可以CI阅读源码、审核commit信息和PR等的形式，自动化地辅助开源开发流程

   难点：是否能用接口访问Github Pull Request？大模型需要读取Pull Request的信息，需要提供接口。大模型的分析结果应当作为建议，而不是代码审核的硬性标准。需要后端开发者调用API获取文本信息，并且输入逻辑结构。

   如果要判断commit message是否符合格式，需要考虑是否严格符合，若不严格可使用大模型。语义信息可以使用大模型识别。

   （🌟是一个比较实际的工业项目）

- 商业端应用

1. 根据云计算、边缘计算的需求智能地调控平台设备，达到功耗、算力和经济效益的最大化

   这应当是调度算法解决的问题，如流量控制算法，属于延迟敏感场景，不应当使用大模型。大模型阅读文本都需要考虑代码长度和通用性。
