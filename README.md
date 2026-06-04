[README.md](https://github.com/user-attachments/files/28587870/README.md)
# NetCanvas
一键信息收集
# NetCanvas 🎯

**一站式网络资产测绘与攻击面管理平台**

NetCanvas 是一款面向安全团队的网络资产发现、管理与攻击面评估平台，将企业信息收集、子域名枚举、资产测绘、漏洞扫描、敏感信息监控等能力整合于一体，提供从信息收集到攻击面管理的完整工作流。

---

## ✨ 核心特性

### 🔍 多维资产发现

- **企业信息收集** — ICP 备案查询、爱企查子公司/APP/微信公众号/小程序采集、0.zone 情报补充
- **域名扩展** — 多源被动子域名收集（crt.sh / RapidDNS / HackerTarget / URLScan.io），DNS 解析验证与通配符过滤
- **资产测绘** — 集成 FOFA、Hunter、Quake、Shodan、Censys、ZoomEye、0.zone 等主流网络空间搜索引擎
- **C 段扩展** — 按 IP 密度排序的 C 段资产发现，自动排除云/CDN 噪声
- **边缘资产发现** — 证书关联、反向 DNS、Favicon 哈希、关联域名等多维度边缘资产探测
- **主动扫描** — 子域名爆破、端口扫描、站点信息采集

### 🧠 一键自动化流水线

一键采集功能将完整资产收集流程编排为 7 个自动化阶段：

1. **企业信息收集** → ICP 查询 + 子公司递归 + APP/微信采集
2. **域名多源扩展** → 被动子域名收集 + DNS 验证
3. **资产测绘收集** → 多平台并发查询（域名/Cert/ICP/WOIS/Favicon）
4. **C 段扩展** → 云 IP 降噪 + 密度排序
5. **存活探测与富化** → HTTP 探活 + 指纹识别
6. **敏感信息探测** → GitHub 代码泄露 + FOFA 暴露服务
7. **验证与汇总** → 资产归属验证 + 差异计算

### 🗺️ 可视化分析

- **仪表盘** — 资产统计卡片、端口分布柱状图、来源分布饼图
- **地理分布** — 基于 Leaflet 的资产地理位置地图
- **拓扑关系** — 基于 D3.js 力导向的域名-IP-端口关系拓扑图
- **资产差异** — 多批次扫描结果对比，快速识别新增/消失资产

### 🔐 安全情报

- **代码泄露监控** — GitHub 代码泄露关键词 Dork 扫描
- **凭据泄露检测** — 凭据泄露信息监控与告警
- **敏感路径扫描** — 敏感文件与路径探测
- **DNS 记录管理** — DNS 解析记录查询与追踪
- **WHOIS 查询** — 域名注册信息与注册人反查
- **漏洞关联** — CVE 漏洞信息关联与查询
- **PoC 管理** — 漏洞验证脚本管理与执行

### ⚙️ 自动化与集成

- **工作流引擎** — 自定义多步骤扫描工作流，支持预设模板
- **定时任务** — Cron 表达式驱动的周期性自动化扫描
- **AI 辅助分析** — 接入大语言模型，智能分析资产风险与高价值目标
- **自定义 API** — 灵活接入第三方资产数据源
- **指纹规则库** — 可扩展的 Web 指纹识别规则，支持多来源规则同步
- **WebSocket 通知** — 实时任务进度推送与告警

### 🏗️ 项目化管理

- 多项目管理，独立维护资产与任务
- 资产标签、收藏、备注
- CDN/WAF 识别标注
- 审计日志全程可追溯
- 数据导入/导出

---

## 🏗️ 技术架构

```
NetCanvas/
├── backend/                 # Python 后端
│   ├── app/
│   │   ├── api/            # FastAPI 路由层 (20+ API 模块)
│   │   ├── collectors/     # 数据采集器 (ICP/爱企查/证书透明度/子域名)
│   │   ├── core/           # 核心组件 (认证/DNS/HTTP客户端/AI客户端)
│   │   ├── models/         # SQLAlchemy 数据模型
│   │   ├── providers/      # 搜索引擎适配器 (FOFA/Hunter/Quake/Shodan/Censys/ZoomEye/0.zone)
│   │   ├── schemas/        # Pydantic 数据校验
│   │   └── services/       # 业务逻辑层 (30+ 服务模块)
│   ├── config.yaml         # 配置文件
│   └── requirements.txt    # Python 依赖
│
├── frontend/                # React 前端
│   ├── src/
│   │   ├── api/            # API 客户端
│   │   ├── components/     # 通用组件
│   │   ├── contexts/       # React Context (认证)
│   │   ├── hooks/          # 自定义 Hooks (WebSocket/i18n)
│   │   ├── locales/        # 中文国际化
│   │   ├── pages/          # 27 个页面模块
│   │   ├── types/          # TypeScript 类型定义
│   │   └── utils/          # 工具函数
│   └── package.json        # 前端依赖
│
└── docker-compose.yml       # Docker 编排
```

### 技术栈

| 层级 | 技术 |
|------|------|
| **前端** | React 19 + TypeScript 6 + Vite 8 + Tailwind CSS 4 + shadcn/ui |
| **图表** | Recharts + D3.js (力导向拓扑) + Leaflet (地理地图) |
| **后端** | FastAPI + Uvicorn + SQLAlchemy 2 (async) + Pydantic 2 |
| **数据库** | SQLite (aiosqlite 异步驱动) |
| **通信** | REST API + WebSocket 实时推送 |
| **部署** | Docker + Docker Compose + Nginx |

---

## 🚀 快速开始

### Docker 部署（推荐）

```bash
# 克隆项目
git clone https://github.com/your-repo/NetCanvas.git
cd NetCanvas

# 一键启动
docker-compose up -d

# 访问
# 前端: http://localhost
# 后端 API: http://localhost:8000
# API 文档: http://localhost:8000/docs
```

### 本地开发

#### 后端

```bash
cd backend

# 安装依赖
pip install -r requirements.txt

# 安装 Playwright 浏览器（用于截图等功能）
playwright install chromium

# 启动服务
python run.py
```

#### 前端

```bash
cd frontend

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

### 配置

编辑 `backend/config.yaml`，填入所需搜索引擎 API 密钥：

```yaml
fofa_email: ""
fofa_key: ""
hunter_api_key: ""
quake_token: ""
shodan_api_key: ""
censys_api_id: ""
censys_api_secret: ""
zoomeye_api_key: ""
aiqicha_cookie: ""
```

> 无需全部配置，仅填入已拥有的平台密钥即可使用对应功能。

---

## 📖 功能模块

| 模块 | 路径 | 说明 |
|------|------|------|
| 仪表盘 | `/dashboard` | 项目资产概览与统计图表 |
| 项目管理 | `/projects` | 多项目隔离管理 |
| 搜索引擎 | `/search` | 多平台资产搜索 |
| 企业扫描 | `/company-scan` | 企业信息与子公司采集 |
| 域名扫描 | `/domain-scan` | 子域名枚举与验证 |
| 主动扫描 | `/active-scan` | 端口扫描与站点探测 |
| 边缘发现 | `/edge-discover` | 关联资产深度发现 |
| 资产浏览器 | `/assets` | 资产查询、筛选与管理 |
| 地理地图 | `/geo-map` | 资产全球地理分布 |
| 拓扑图 | `/topology` | 域名-IP-端口关系可视化 |
| 资产差异 | `/asset-diff` | 扫描批次对比 |
| 代码泄露 | `/code-leaks` | GitHub 代码泄露监控 |
| 凭据泄露 | `/credential-leaks` | 凭据泄露检测 |
| DNS 记录 | `/dns-records` | DNS 解析记录查询 |
| WHOIS | `/whois` | 域名注册信息查询 |
| 漏洞管理 | `/vulnerabilities` | CVE 漏洞关联 |
| PoC 管理 | `/poc` | 漏洞验证脚本管理 |
| 工作流 | `/workflows` | 自定义扫描工作流 |
| 定时任务 | `/schedules` | 周期性自动化调度 |
| 指纹规则 | `/fingerprint-rules` | Web 指纹识别规则管理 |
| 规则库源 | `/library-sources` | 指纹规则远程源同步 |
| 自定义 API | `/custom-providers` | 第三方数据源接入 |
| AI 设置 | `/ai-settings` | 大语言模型集成配置 |
| 审计日志 | `/audit-log` | 操作审计追踪 |
| 系统设置 | `/settings` | 平台配置管理 |

---

## 🔌 支持的搜索引擎

| 平台 | 官网 | 特点 |
|------|------|------|
| **FOFA** | fofa.info | 国内最大网络空间搜索引擎 |
| **Hunter** | hunter.qianxin.com | 奇安信网络空间测绘 |
| **Quake** | quake.360.net | 360 网络空间测绘 |
| **Shodan** | shodan.io | 全球知名 IoT 搜索引擎 |
| **Censys** | censys.io | 证书与主机扫描 |
| **ZoomEye** | zoomeye.org | 知道创宇网络空间搜索 |
| **0.zone** | 0.zone | 企业情报与资产搜索 |
| **自定义** | — | 支持自定义 API 数据源接入 |

---

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 参与项目建设。

---

## 📄 许可证

[MIT License](LICENSE)
