# 安装依赖，根据系统（Ubuntu 24.04、HCE2.0）不同选择相应的脚本

## 代码下载

```markdown
# 克隆仓库
git clone https://github.com/mem0ai/mem0.git

# 进入到openmeory目录下
cd openmemory

# 配置镜像源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple


# 为 API 和 UI 配置环境变量
cp api/.env.example api/.env
```

## 配置api/.env

~~~markdown
# Primary OpenAI API key for general use.
OPENAI_API_KEY=sk-xxx
USER=root

# --- Optional Configurations for Categorization Feature ---
# The configuration here will be applied to openmemory\api\app\utils\categorization.py
# Uncomment and set if you have a specific endpoint for categorization.
CATEGORIZATION_OPENAI_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1

# Uncomment and set if you have a specific API key for categorization tasks.
CATEGORIZATION_OPENAI_API_KEY=sk-xxx

# Uncomment and set if you want to use a specific model for categorization.
CATEGORIZATION_OPENAI_MODEL=qwen-max
# 

# ------ Optional Configurations for Memory ------
# In openmemory\api\app\utils\memory.py, you'll find the initialization of the LLM and embedder models.
# These are optional configurations.
# "When customizing LLM models, please remember to synchronously modify the OPENAI_API_KEY"

# Uncomment and set if you have a specific endpoint for llm.
OPENAI_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1

# Uncomment and set if you want to use a specific model for llm model.
OPENAI_MODEL=qwen-plus

# Uncomment and set if you have a specific endpoint for embedding model.
OPENAI_EMBEDDING_MODEL_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1

# Uncomment and set if you have a specific API key for embedding model.
OPENAI_EMBEDDING_MODEL_API_KEY=sk-xxxx

# Uncomment and set if you want to use a specific model for embedding model.
OPENAI_EMBEDDING_MODEL=text-embedding-v2

# Uncomment and set if you want to use a specific dimension for embedding model.
OPENAI_EMBEDDING_MODEL_DIMS=1536

# ------ Database for Memory ------
# Uncomment and set if you want to use a specific database for memory.
# The default is SQLite, but you can change it to PostgreSQL or any other database supported by SQLAlchemy.
# DATABASE_URL=postgresql://username:password@ip:5432/openmemory
# DATABASE_URL=mysql+pymysql://username:password@ip:3306/openmemory
~~~



## 配置ui下 .env的配置

```
cp ui/.env.example ui/.env
NEXT_PUBLIC_API_URL=http://openmemory-mcp:8765
NEXT_PUBLIC_USER_ID=$(whoami)
```

## 修改docker-compose.yaml文件

~~~markdown
services:
  mem0_store:
    image: qdrant/qdrant
    ports:
      - "6333:6333"
    volumes:
      - mem0_storage:/mem0/storage
    restart: always     # ✅ 自动重启

  openmemory-mcp:
    image: mem0/openmemory-mcp
    build: api/
    environment:
      - USER
      - API_KEY
    env_file:
      - api/.env
    depends_on:
      - mem0_store
    ports:
      - "8765:8765"
    volumes:
      - ./api:/usr/src/openmemory
    command:
      sh -c "uvicorn main:app --host 0.0.0.0 --port 8765 --reload --workers 4"
    restart: always     # ✅ 自动重启

  openmemory-ui:
    build:
      context: ui/
      dockerfile: Dockerfile
    image: mem0/openmemory-ui:latest
    ports:
      - "3000:3000"
    env_file:
      - ui/.env
    environment:
      - NEXT_PUBLIC_API_URL=${NEXT_PUBLIC_API_URL}
      - NEXT_PUBLIC_USER_ID=${USER}
    restart: always     # ✅ 自动重启

volumes:
  mem0_storage:

~~~



## 启动服务

~~~markdown
# 使用以下命令启动该项
export NEXT_PUBLIC_USER_ID=$(whoami)
export USER=$(whoami)
export NEXT_PUBLIC_API_URL=http://localhost:8765
# 构建项目
docker compose  build --no-cache
# 启动项目
docker compose up -d
~~~

