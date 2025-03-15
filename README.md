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

本项目采用以下核心技术：

- **数据库**: PostgreSQL - 强大的分析能力和开源特性，支持复杂数据类型和查询需求
- **ORM**: SQLAlchemy - Python生态系统中最成熟的ORM，提供灵活的数据建模和查询能力
- **后端语言**: Python - 强大的数据处理和机器学习生态系统，广泛的库和工具支持
- **ETL工具**: Apache Airflow - 工作流编排工具，满足复杂ETL流程需求
- **API框架**: FastAPI - 高性能异步Python API框架，自动文档生成和类型验证
- **机器学习**: Scikit-learn, PyTorch - 机器学习和深度学习模型的开发和部署
- **可视化**: Power BI - 商业智能工具，通过PostgreSQL连接器支持与我们的数据库集成
- **云平台**: AWS - 提供弹性可扩展的服务，包括EC2、RDS、S3等核心组件
- **缓存**: Memcached - 轻量级、高性能的分布式内存缓存系统，用于应用级缓存
- **容器化**: Docker & Docker Compose - 支持一致的开发和生产环境
- **CI/CD**: GitHub Actions - 自动化测试和部署流程，与GitHub仓库集成

每项技术选择的详细理由、考虑的替代方案以及具体实施细节，请参阅[技术栈决策文档](docs/6-tech-stack-decisions.md)。

## 设计文档导航

本项目采用结构化文档策略，每个文档都有明确的焦点和责任范围，共同构成完整的系统设计：

0. [需求文档](docs/0-requirements.md)
   - 项目背景与目标
   - 功能需求（数据采集、处理存储、分析预测、用户界面、API服务）
   - 非功能性需求（性能、安全、可扩展性、可维护性）
   - 用户场景与使用案例
   - 项目边界与假设
   - 验收标准
   - 交付成果与项目规划

1. [架构设计](docs/1-architecture.md)
   - 系统整体架构和组件关系的高层概述
   - 分层设计与数据流向
   - 各层次功能和交互的总体视图
   - 系统限制与扩展性考虑
   - 引导读者到其他文档获取详细信息

2. [ETL流程](docs/2-ETL-Pipeline.md)
   - 数据提取策略和方法
   - 数据转换逻辑和流程
   - PostgreSQL数据加载和SQLAlchemy集成
   - 数据质量检查机制
   - Airflow工作流编排
   - 监控与日志设计
   - 灾难恢复和容错机制

3. [数据模型](docs/3-database-schema.md)
   - PostgreSQL星型模式数据设计
   - 维度表和事实表详细结构
   - 索引和分区策略优化
   - SQLAlchemy ORM映射
   - 数据版本控制和血缘追踪
   - 存储估算和优化方案
   - 未来扩展方向

4. [缓存策略](docs/4-caching-strategy.md)
   - 多层缓存架构设计
   - Memcached应用级缓存实现
   - SQLAlchemy查询缓存集成
   - PostgreSQL物化视图策略
   - 缓存失效和监控方案
   - 安全考虑和恢复策略
   - 性能分析和优化指标

5. [运维策略](docs/5-operations.md)
   - 环境分离和配置管理
   - 高可用架构设计与实现
   - 全面的监控告警系统
   - 安全策略和访问控制
   - CI/CD自动化部署流程
   - 备份恢复与灾难应对
   - 成本优化与资源规划
   - 系统持续改进策略

6. [技术栈决策](docs/6-tech-stack-decisions.md)
   - 各技术选择的详细理由
   - 替代方案分析与比较
   - 技术兼容性和集成考虑
   - 版本选择和兼容性管理
   - 技术栈演进路径

7. [实施路线图](docs/7-implementation-roadmap.md)
   - 项目阶段划分与时间线
   - 各阶段详细任务和里程碑
   - 资源需求和团队组成
   - 风险分析与缓解策略
   - 成功指标和后续规划

8. [开发规范与Git工作流](docs/8-development-guidelines.md)
   - 代码风格与格式规范
   - Git分支管理策略和工作流程
   - 提交消息规范
   - 代码审查流程
   - 测试要求
   - 本地开发环境配置
   - 文档更新要求
   - 版本控制策略
   - 依赖管理

## 代码仓库结构

```
nba-fantasy-analytics-platform/
├── .github/                    # GitHub配置和工作流
│   └── workflows/              # CI/CD工作流定义
├── docs/                       # 文档
│   ├── api/                    # API文档
│   └── diagrams/               # 设计图表
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
- Memcached 1.6+
- Docker & Docker Compose

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
   docker-compose up -d db memcached
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

这将启动所有服务，包括API、PostgreSQL数据库、Memcached缓存和Airflow调度器。

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
