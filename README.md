# 购车深度调研

基于第一性原理的汽车购买决策分析工具。

## 使用方式

通过 Skill 调用：提供候选车型列表，自动执行 6 阶段深度调研流程。

## 项目结构

```
car-research/
├── SKILL.md                 # Skill 定义
├── framework/               # 可复用方法论
│   ├── first-principles.md  # 五层决策框架
│   ├── analysis-methodology.md  # 六阶段流程定义
│   └── search-matrices.md   # 搜索词模板库
└── {instance}/              # 调研实例（每次调研一个目录）
```

## 调研流程

```
Phase 0: 建立决策框架（五层模型）
Phase 1: 候选车基础档案（每车独立 Agent）
Phase 2: 负面信息专项（每车独立 Agent，与 Phase 1 完全隔离）
Phase 3: 安全事故率标准化（事故数 ÷ 保有量）
Phase 4: 行业销量与数据置信度
Phase 5: 横向对比表（按五层框架）
Phase 6: 最终决策矩阵（加权评分 + 敏感性分析 + 决策树）
```

## 调研实例

| 时间 | 主题 | 候选车 | 结论 |
|------|------|--------|------|
| [2026-04](2026-04-七车对比/) | 七车对比 | SU7、YU7、Model Y、ET5、ES6、007GT、001 | SU7 > 007GT > ET5 > 001 > YU7 > Model Y > ES6（默认权重） |
