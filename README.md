## 第四届博览医书杯封闭赛道开源数据
**队长：** 张剑昆
**机构：** 中国科学院软件研究所

文件结构：
- /code：用于环境搭建的相关文件
- /data：知识库数据

### 部署启动
1. 环境准备
   - 按官方教程部署milvus
   - 按官方教程部署xinference
   - 按官方教程部署dify **注意：** 此处可能需要修改官方docker-compose.yaml文件，为每个容器配置访问宿主机端口的能力（为了访问xinference和milvus）
   - 克隆github项目：https://github.com/onenov/Dify2OpenAI（实现类OpenAI接口的方式访问dify），并于项目根目录下放置 /code/Dockerfile 和 /code/docker-compose.yaml ，以实现项目镜像打包和docker部署
   - 在dify中安装访问xinference和milvus的插件，并配置：一个名为 **Qwen3-8B** 的模型和一个名为 **Qwen3-Embedding-4B** 的模型，以及连接milvus数据库后端
   - 以DSL文件（/code/封闭赛道(work).yml）导入的方式创建工作流
2. 知识库准备
   修改 /code/build_env.ipynb 代码文件中的文件路径及milvus访问地址，然后分别执行两个代码块，实现实体库、三元组库以及病案库的搭建
3. 启动推理 **注意：** 此处需要访问 Dify2OpenAI 项目的服务地址（正常是localhost的3099端口），提供dify工作流的API key，并指定模型名称为 **dify|Chat|Dify访问路径||answer**
