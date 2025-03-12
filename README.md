# NBA Fantasy Analytics Platform

## 项目概述

NBA Fantasy Analytics Platform是一个端到端的数据分析平台，为Fantasy篮球玩家提供数据驱动的决策支持工具。该平台从NBA数据采集、处理、分析到可视化呈现，帮助用户做出更明智的Fantasy篮球决策。

### 核心功能

- **数据采集**: 从多个来源自动收集NBA球员和比赛数据
- **数据转换**: 将原始数据处理为分析友好的格式
- **预测分析**: 使用机器学习模型预测球员表现和Fantasy得分
- **阵容优化**: 基于预测和比赛对阵分析生成最优阵容建议
- **可视化仪表板**: 通过Power BI提供直观的数据分析界面
- **API接口**: 提供程序化访问平台功能的方式

## 技术栈选择

经过评估，本项目采用以下核心技术：

- **数据库**: PostgreSQL - 选择原因包括开源免费、强大的分析能力、良好的扩展性以及与AWS的兼容性
- **ORM**: SQLAlchemy - Python生态系统中最强大的ORM，提供灵活的数据建模和查询能力
- **后端语言**: Python - 强大的数据处理和机器学习能力，广泛的库和工具支持
- **ETL工具**: Apache Airflow - 强大的工作流编排工具，适合复杂ETL流程管理
- **API框架**: FastAPI - 高性能异步Python API框架，具有自动文档生成功能
- **机器学习**: Scikit-learn, PyTorch - 行业标准的ML工具，适合不同复杂度的模型
- **可视化**: Power BI - 功能强大的BI工具，通过PostgreSQL连接器支持与我们的数据库集成
- **云平台**: AWS - 提供灵活可扩展的服务，包括EC2、RDS、S3等
- **缓存**: Redis - 高性能内存数据库，用于缓存和会话管理
- **容器化**: Docker & Docker Compose - 简化开发和部署流程
- **监控**: Prometheus & Grafana - 全面的系统监控和可视化
- **CI/CD**: GitHub Actions - 自动化测试和部署流程

## 设计文档导航

本代码库包含以下设计文档，详细描述了平台的各个方面：

1. [架构设计](docs/diagrams/1-architecture.md)
   - 系统整体架构和组件关系
   - 技术栈选择与决策理由
   - AWS部署模型和服务通信
   - API设计和端点规范
   - 扩展性、性能优化和安全考虑

2. [ETL流程](docs/diagrams/2-ETL-Pipeline.md)
   - 数据提取策略和方法
   - 数据转换逻辑和流程
   - PostgreSQL数据加载和SQLAlchemy集成
   - 数据质量检查机制
   - Airflow工作流编排
   - 监控与日志设计
   - 灾难恢复和容错机制

3. [数据模型](docs/diagrams/3-database-schema.md)
   - 星型模式数据设计
   - 维度表和事实表详细结构
   - PostgreSQL特有索引策略
   - 分区方案和自动化维护
   - 数据血缘和版本控制
   - SQLAlchemy ORM映射
   - 存储估算和优化

4. [缓存策略](docs/diagrams/4-caching-strategy.md)
   - 多层缓存架构设计
   - Redis应用级缓存实现
   - SQLAlchemy查询缓存集成
   - PostgreSQL物化视图策略
   - 缓存失效和监控方案
   - 安全考虑和灾难恢复

5. [运维策略](docs/diagrams/5-operations.md)
   - 环境分离和配置管理
   - PostgreSQL高可用架构
   - 监控告警和日志管理
   - 安全策略和访问控制
   - 部署流程和变更管理
   - PostgreSQL备份恢复和维护
   - 成本优化和持续改进

6. [实施路线图](docs/diagrams/implementation-roadmap.md)
   - 项目阶段划分与时间线
   - 各阶段详细任务和里程碑
   - 资源需求和团队组成
   - 风险分析与缓解策略
   - 成功指标和后续规划

## 代码仓库结构

```
nba-fantasy-analytics-platform/
├── .github/                    # GitHub配置和工作流
│   └── workflows/              # CI/CD工作流定义
├── docs/                       # 文档
│   ├── api/                    # API文档
│   └── diagrams/               # 设计文档
├── src/                        # 源代码
│   ├── api/                    # FastAPI应用
│   │   ├── routers/            # API路由
│   │   ├── models/             # API模型
│   │   └── dependencies/       # API依赖
│   ├── core/                   # 核心业务逻辑
│   │   ├── analytics/          # 分析引擎
│   │   ├── prediction/         # 预测模型
│   │   └── services/           # 业务服务
│   ├── data/                   # 数据处理
│   │   ├── etl/                # ETL流程
│   │   ├── sources/            # 数据源连接器
│   │   └── validation/         # 数据验证
│   ├── db/                     # 数据库
│   │   ├── migrations/         # Alembic迁移脚本
│   │   ├── models/             # ORM模型
│   │   └── repositories/       # 数据访问层
│   ├── cache/                  # 缓存管理
│   └── utils/                  # 通用工具函数
├── tests/                      # 自动化测试
│   ├── unit/                   # 单元测试
│   ├── integration/            # 集成测试
│   └── fixtures/               # 测试数据固定装置
├── airflow/                    # Airflow DAG定义
├── scripts/                    # 实用脚本
├── docker/                     # Docker配置
│   ├── api/                    # API服务Docker配置
│   ├── worker/                 # 后台工作者Docker配置
│   └── db/                     # PostgreSQL Docker配置
├── infrastructure/             # 基础设施代码
│   ├── terraform/              # Terraform IaC配置
│   └── scripts/                # 部署和维护脚本
├── powerbi/                    # Power BI相关文件
│   ├── templates/              # 报表模板
│   └── queries/                # DAX查询
├── requirements/               # 依赖管理
│   ├── base.txt                # 基础依赖
│   ├── dev.txt                 # 开发依赖
│   └── prod.txt                # 生产依赖
├── .env.example                # 环境变量示例
├── docker-compose.yml          # 本地开发Docker编排
├── Makefile                    # 常用命令
├── setup.py                    # 包安装配置
├── pyproject.toml              # Python项目配置
├── .gitignore                  # Git忽略文件
└── README.md                   # 项目说明文档
```

## 安装与运行

### 系统要求

- Python 3.10+
- PostgreSQL 14.0+
- Redis 6.0+
- Docker & Docker Compose (推荐)

### 本地开发环境设置

1. 克隆仓库
   ```bash
   git clone https://github.com/yourusername/nba-fantasy-analytics-platform.git
   cd nba-fantasy-analytics-platform
   ```

2. 设置虚拟环境
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   # 或
   venv\Scripts\activate  # Windows
   ```

3. 安装依赖
   ```bash
   pip install -r requirements/dev.txt
   ```

4. 设置环境变量
   ```bash
   cp .env.example .env
   # 编辑.env文件，配置必要的环境变量
   ```

5. 使用Docker启动依赖服务
   ```bash
   docker-compose up -d db redis
   ```

6. 运行数据库迁移
   ```bash
   alembic upgrade head
   ```

7. 启动开发服务器
   ```bash
   uvicorn src.api.main:app --reload
   ```

8. 访问API文档：http://localhost:8000/docs

### 使用Docker Compose

完整系统启动:
```bash
docker-compose up -d
```

这将启动所有服务，包括API、PostgreSQL数据库、Redis缓存和Airflow调度器。

## 数据库迁移

使用Alembic管理数据库迁移:

```bash
# 创建新迁移
alembic revision --autogenerate -m "描述变更"

# 应用迁移
alembic upgrade head

# 回滚迁移
alembic downgrade -1
```

## 常见问题

<details>
<summary>如何添加新的数据源?</summary>

在`src/data/sources/`目录下创建新的数据采集器，然后在ETL管道中注册它。具体实现应遵循接口约定，详细步骤请参考ETL流程文档。
</details>

<details>
<summary>如何创建自定义报表?</summary>

使用Power BI Desktop连接到PostgreSQL数据库，然后利用星型模式创建所需的分析视图。连接配置请参考缓存策略文档中的数据库访问部分。
</details>

<details>
<summary>系统扩容方案?</summary>

对于增长的用户负载，可以通过Auto Scaling组增加EC2实例数量，升级RDS PostgreSQL实例类型，或添加PostgreSQL只读副本来扩展数据库读取容量。详情请参考运维策略文档的高可用架构部分。
</details>

<details>
<summary>如何监控系统性能?</summary>

系统集成了全面的监控解决方案，包括CloudWatch监控AWS资源、PostgreSQL特有监控指标、API性能监控和自定义业务指标。详细配置请参考运维策略文档的监控与警报部分。
</details>

## 项目状态

这是一个个人项目，目前处于开发阶段。如有兴趣了解更多或提供建议，欢迎通过提交Issue的方式交流。

## 许可证

[MIT License](LICENSE)
