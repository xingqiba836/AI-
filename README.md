#   Web平台人工智能旅行助手

## 项目简介

AI 旅行规划师是一款智能旅行规划应用，通过 AI 技术帮助用户自动生成个性化旅行路线，提供费用预算管理和地图导航功能。



## 核心功能

- 智能行程规划：支持语音/文字输入，AI 自动生成个性化旅行路线，相对日期模式支持
- 费用预算管理：智能预算分析、语音记账、费用统计图表与预算预警
- 用户管理系统：注册登录、多份行程保存与云端同步、个人资料管理
- 地图导航集成：高德地图可视化、景点标记、路线连接、方向指示
- 数据可视化：行程时间轴、费用分类饼图、每日趋势图、预算进度条

## 技术栈


### 后端服务
- **Next.js API Routes** - 后端 API 接口
- **Supabase** - 数据库（PostgreSQL）与用户认证
### 前端框架
- **Next.js 15**（App Router）- React 全栈框架
- **React 19** - 最新特性
- **TypeScript 5** - 类型安全
- **Tailwind CSS 3** - 样式框架
- **shadcn/ui** - 现代 UI 组件库
- **Recharts** - 数据可视化图表
### 第三方服务
- **科大讯飞 Web API** - 语音识别功能
- **高德地图 JavaScript API** - 地图展示与导航
- **DeepSeek API** - 大语言模型（行程规划与费用预算）
### 开发工具
- **ESLint & Prettier** - 代码规范
- **Husky** - Git hooks
- **Docker** - 容器化部署

## 环境要求


### API Keys 配置
项目运行需要以下 API Keys（请自行申请）：

#### 必需的 API Keys
1. **Supabase**（用户认证和数据库）
   - 项目 URL
   - Anon Key

2. **DeepSeek**（AI 行程规划）
   - API Key

3. **科大讯飞**（语音识别）
   - App ID
   - API Key  
   - API Secret

4. **高德地图**（地图导航）
   - Web端（JS API）Key - 用于地图显示
   - Web服务 API Key - 用于地理编码



## 🐳 Docker 快速部署

### ⚡ 快速开始

本项目提供已打包好的 Docker 镜像，开箱即用。

#### 前置要求

- ✅ 安装 Docker Desktop: 
- ✅ 确保 Docker 正在运行

#### 步骤 1：导入镜像

```bash
docker load -i ai-travel-planner-docker-image.tar
```


#### 步骤 2：创建环境变量文件

在镜像文件同目录创建 `.env` 文件：

```env
DEEPSEEK_API_KEY=your_deepseek_api_key
AMAP_WEB_SERVICE_KEY=your_amap_web_service_key
```

**说明**：
- 这两个 API Key 需自行申请（免费）
- 其他所有配置已内置在镜像中
- 详细申请步骤见下文

#### 步骤 3：启动应用

**方法 A - 使用 docker run**（简单直接）：

```bash
docker run -d --name ai-travel-planner -p 3000:3000 \
  -e DEEPSEEK_API_KEY=your_deepseek_api_key \
  -e AMAP_WEB_SERVICE_KEY=your_amap_web_service_key \
  ai-travel-planner:latest
```

**Windows PowerShell**：
```powershell
docker run -d --name ai-travel-planner -p 3000:3000 `
  -e DEEPSEEK_API_KEY=your_deepseek_api_key `
  -e AMAP_WEB_SERVICE_KEY=your_amap_web_service_key `
  ai-travel-planner:latest
```

**方法 B - 使用 docker-compose**（推荐）：

创建 `docker-compose.yml`：
```yaml
version: '3.8'
services:
  app:
    image: ai-travel-planner:latest
    container_name: ai-travel-planner
    ports:
      - "3000:3000"
    env_file:
      - .env
    restart: unless-stopped
```

启动：
```bash
docker-compose up -d
```

#### 步骤 4：访问应用

打开浏览器：**http://localhost:3000**

---
### 📋 功能清单

- [ ] 用户注册和登录
- [ ] AI 生成旅行计划（需 DeepSeek Key）
- [ ] 语音输入（需浏览器麦克风权限）
- [ ] 地图导航（景点标记、连线、箭头）
- [ ] 费用管理和统计

---



### 💡 重要说明

**已内置在镜像中**（无需配置）：
- ✅ Supabase（数据库）
- ✅ 科大讯飞（语音识别）
- ✅ 高德地图（地图显示）

**需要运行时提供**（仅2个）：
- 🔧 `DEEPSEEK_API_KEY` - AI 行程规划
- 🔧 `AMAP_WEB_SERVICE_KEY` - 地理编码服务
