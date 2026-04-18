# rag_qa_assistant_v1
### 1.项目简介：
这是一个最小版的 RAG（Retrieval-Augmented Generation）知识库问答助手。  
  
项目会先从本地文档中检索与用户问题最相关的文本片段，再将这些片段作为参考上下文发送给大语言模型生成回答，并同时展示参考片段，便于查看回答依据。
### 2.项目功能：
当前版本支持以下功能
- 读取本地文档切分后的‘chunks.json'
- 使用TF-IDF+余弦相似度进行检索
- 返回top-3最相关的参考片段
- 将”用户问题+检索结构“一起发给大模型生成回答
- 打印输出答案以及参考片段
### 3.技术栈：
- Python
- scikit-learn
- TF-IDF
- cosine similarity
- OpenAI Python SDK
- DeepSeek API
- JSON
### 4.项目结构：
```text  
rag_qa_assistant_v1/  
├── qa_assistant.py # 主程序：检索 + 生成问答  
├── doc_chunker.py # 文档切分脚本（文档需自己提供）  
├── retrieval_demo.py # 最小检索演示脚本  
├── chunks1.json # 切分后的文档片段  
├── README.md # 项目说明
```
### 5.运行方式：
qa_assistant.py为主程序
##### 1）安装依赖
pip install openai scikit-learn
#### 2）配置环境变量
- DEEPSEEK_API_KEY
- DEEPSEEK_BASE_URL

```示例
set DEEPSEEK_API_KEY=你的key  
set DEEPSEEK_BASE_URL=https://api.deepseek.com
```
#### 3）运行主程序
``` Bash
python qa_assistant.py

```
### 6.输入输出说明：
#### 输入：
- 用户问题
- 可选的额外回答要求
#### 输出：
- 大模型生成的最终回答  
- top-3 检索到的参考片段  
- 每个参考片段对应的来源、chunk 编号和相似度分数


### 运行示例  
  
#### 输入问题  
rag是什么  
#### 输入要求
回答完整，字数简洁
  
#### 输出效果  
RAG是检索增强生成（Retrieval-Augmented Generation），指先从自有资料中检索相关内容，再交给模型生成回答，以提高回答的准确性和针对性，避免仅依赖模型固有知识或冗长提示。
  
![[结果.png]]