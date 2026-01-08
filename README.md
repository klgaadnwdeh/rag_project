rag_project
RAG 知识问答系统

一个面向企业知识库场景的检索增强生成（RAG）系统，支持多格式文档上传、智能分块、混合检索与查询优化，实现高精度、可溯源的自然语言问答。

📌 项目简介

本项目构建了一个端到端的 RAG（Retrieval-Augmented Generation）问答系统，旨在解决企业内部非结构化文档（如 PDF、Word、TXT 等）难以高效检索与问答的问题。系统通过智能文本切分、多策略向量化索引、混合检索排序及查询重写等技术，显著提升问答准确性与用户体验。

核心特点：

✅ 支持多格式文档自动解析与语义分块

✅ 基于 Qwen Embedding 的高质量向量表示

✅ 混合检索：融合 BM25、TF-IDF 与稠密向量排序

✅ 查询优化：问题重述、子问题拆解、元数据引导

✅ 可评估、可扩展、具备生产部署潜力

实测指标：召回率 90% | 精确率 80% | F1 值 85%

🧩 核心功能

智能文档处理 自动识别文件类型（PDF/DOCX/TXT 等）

针对不同内容类型采用差异化分块策略：

问答类数据 → 固定长度字符切分

常规文档 → RecursiveCharacterTextSplitter（512/128）

多维向量索引

使用 Qwen Embedding 模型生成文本向量

构建三类索引提升检索能力：

原始文本向量索引

段落摘要索引（用于语义压缩）

元数据索引（支持按来源、章节等过滤）

混合检索架构

稀疏检索：BM25 + TF-IDF（关键词匹配）

稠密检索：向量相似度（余弦距离）

融合排序：加权融合多路结果，提升 top-k 相关性

查询理解与优化

问题重述：将模糊或指代性问题转为明确检索语句

子问题拆解：复杂问题分解为多个原子查询

元数据引导：自动提取时间、实体等信息约束检索范围

🚀 快速开始

环境依赖

Python ≥ 3.9

ChromaDB（向量存储）

LangChain（文档加载与链式调用）

Qwen API（Embedding 与 LLM 推理）

安装 bash git clone https://github.com/klgaadnwdeh/rag_project.git 

cd rag-knowledge-qa 

pip install -r requirements.txt

下来直接运行main.py文件即可

了解项目结构，有助于您们梳理清楚整体的逻辑结构的,查看文档的项目结构在/asserts/structure.txt，同时还是可以查看对应的加载文档的图片内容的。

📊 效果评估

我们采用 Ragas 框架对系统进行离线评估，关键指标如下： 指标 数值 Recall（召回率） 90%

Precision（精确率） 80%

F1 Score 85%

Faithfulness（事实一致性） >0.9

评估脚本见 ragas_eval.py。

🛠️ 未来计划

支持多轮对话上下文感知检索, 增加用户反馈机制与在线学习闭环, 实现多租户隔离与权限控制, 提供 Docker 镜像与 RESTful API。 📄 许可证

本项目采用 Apache License 2.0 开源协议。

💬 贡献与反馈

欢迎提交 Issue 或 Pull Request！ 如果您在实际业务中使用了本项目，也欢迎分享您的场景与改进建议。
