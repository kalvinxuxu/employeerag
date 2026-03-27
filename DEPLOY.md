# Streamlit on Vercel

由于 Vercel 主要支持静态网站和 Serverless 函数，Streamlit 应用需要通过以下方式部署：

## 方案 1：使用 Vercel 服务器部署（需要 Pro 计划）

1. 在 Vercel 项目中启用 **Functions**
2. 配置 `vercel.json` 使用 Python 运行时
3. 安装依赖并运行 `streamlit run`

## 方案 2：使用 Docker 部署到 Vercel（推荐）

```bash
# 构建 Docker 镜像
docker build -t pdf-rag-system .

# 推送到 Docker Hub
docker push your-username/pdf-rag-system

# 在 Vercel 中配置容器部署
```

## 方案 3：使用其他平台（最简单）

### Railway
```bash
# 安装 Railway CLI
npm i -g @railway/cli

# 登录并创建项目
railway login
railway init

# 添加环境变量
railway add DASHSCOPE_API_KEY=your_key

# 部署
railway up
```

### Render
1. 在 Render 创建新 Web Service
2. 连接 GitHub 仓库
3. 设置启动命令：`streamlit run app.py --server.port $PORT --server.address 0.0.0.0`
4. 添加环境变量 `DASHSCOPE_API_KEY`

### Hugging Face Spaces（免费）
1. 创建新 Space，选择 Streamlit 模板
2. 上传代码或连接 GitHub
3. 在 Settings 中添加 secrets

## 环境变量

部署前请确保设置以下环境变量：

| 变量名 | 说明 |
|--------|------|
| `DASHSCOPE_API_KEY` | 阿里云 DashScope API 密钥 |

## 本地测试

```bash
# 安装依赖
pip install -r requirements.txt

# 设置环境变量
export DASHSCOPE_API_KEY=your_key

# 运行应用
streamlit run app.py
```
