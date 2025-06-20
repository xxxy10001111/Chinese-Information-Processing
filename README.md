# RAG 论文检索与问答系统

**目前实现的流程：**
- 数据层有两个源，一个是 arxiv+github，调用 arxiv API 检索相关主题的论文，在摘要中尝试提取 github 链接，再调 github API 获取一些仓库信息，如 readme、star 数等。另一个源是 paper with code 网站的 api，(https://paperswithcode.com/, https://paperswithcode.com/api/v1/docs/)也是能够进行论文检索，并得到对应的 github 仓库相关信息。
- Rag 部分使用 llamaindex，建立检索块，使用的 embedding 模型是 BAAI\bge-small-en-v1.5，代码里是本地导入了，如果在自己电脑上跑可以连梯子从 huggingface 下载。
- 模型部分用的 deepseek 的 api，框架用的 langchain，能够根据设置的提示词模板封装上下文、历史记录和问题进行回答。
- 前端 app

**接下来需要完善的：**
目前提示词没有怎么优化，只是让它进行论文总结，可以再完善一下让它比较好的生成综述；对代码的分析不好，因为从仓库得到的相关信息不太能支持它读到实际代码。
接下来需要做的大概有：
- 完善提示词
- 找一下看看rag部分的检索有没有别的方法能够做得更好
- 对爬取的相关信息进行更精细的筛选和处理，现在给他的东西只有粗略的论文摘要和 github 的简单的仓库信息。可能需要想办法看怎么喂给它论文内容或者具体代码，优化模型得到的上下文
- 题目要求需要生成海报，我们看这个准备怎么做，我不太熟文生图模型，感觉纯让ds 生成 mermaid 图可能效果不太好
- 最后可以在稍微美化一下前端界面

注：requirements 里的记录可能有缺的，缺哪个直接 pip 就行，没有很难装的库。