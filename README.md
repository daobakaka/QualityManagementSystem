# 质量信息系统概要

## 1. 设计理念

基于企业实际应用的 WEB 开发项目，针对大量生产统计数据进行自动化处理，提取关键数据，结合一键化的质量分析、生产分析、供应分析，全面提升工作处理效率； 
同时聚焦解决质量信息日常处理（数据拉取、筛选、填报、分析等）中的高重复度工作，让 QE 专注于问题本身的追踪、协调与解决。

---

## 2. 技术框架

### 2.1 核心
- **ASP.NET Core Web MVC**
- **EntityFrameworkCore**
- **jQuery**
- **Bootstrap**

### 2.2 辅助
- **xlsx**
- **JSZip**
- **PptxGenJS**
- **Plotly**
- **BCrypt.Net-Next**
- **ClosedXML**
- **CsvHelper**
- **DocumentFormat.OpenXml**
- **EPPlus**

---

## 3. 与通用 CRM 系统的主要区别

1. **定制化功能**：满足 QE 实际需求，支持一键抓取与计算  
2. **定向查询**：如输入车号等基础信息即可快速获取关联数据  
3. **自动化信息处理**：如 SQL 一键纳入、Office 文档自动生成  
4. **进度跟踪与预警**：超期工作在首页滚动提示  
5. **数据强关联**：车号、物料号、PQS 编号等信息互相关联，方便管理  
6. **更短需求周期**：快速响应并实现定制化功能  
7. **小巧灵活**：专注实用性与轻量级部署
8. **依赖性**：依附于CRM，但具备更强的垂直需求解决能力

---

## 4. 质量问题识别原则

- **多维度准入条件**  
  以「车型、物料号、故障频次、MIS（使用月数）」为核心构建筛选机制：  
  - **车型**：聚焦不同车型的特性与潜在故障模式  
  - **物料号**：定位具体零部件，以便甄别重复或批量性问题  
  - **频次**：同一零部件在同一车型下的重复出现次数，超过设定值即视为高风险  
  - **MIS**：在 3mis、6mis、12mis、24mis 等关键使用时段进行监测，若故障集中爆发则需重点关注

- **阈值触发与自动识别**  
  当「车型 + 物料号 + 频次 + MIS」四项指标综合达到预设门槛，系统将问题标记为“需 100% 处理”，并直接进入质量分析或立项流程；若暂未达标，则保留在数据池中，便于后续追溯。

- **新旧问题区分**  
  对符合触发条件的问题先比对历史问题库（如 SIL 清单）：  
  - 已存在则合并处理，避免重复立项  
  - 未记录则判定为新问题，开立新项目或新 SIL 进行深度分析

- **动态预警机制**  
  针对特定 MIS 阶段（如 3mis ≥ 8 条）设定重点监控阈值，一旦超出即进入每日 24 小时会议讨论，确保严重或高频问题能及时获知与响应；阈值可根据车型、批次及企业策略动态调整。

- **持续跟踪与升级**  
  一旦识别为新问题，纳入质量跟踪流程（如周例会、专项会议等），并在后续使用月份（6mis、12mis 等）持续监控；若故障频次上升或范围扩大，则迅速升级处理优先级，调配更多资源完成根因分析与改进闭环。

---

## 5. 系统界面与主要交互

### 5.1 基本界面

![登录页面](https://github.com/user-attachments/assets/18403d38-251f-4a6b-bea0-53574e72c3bd)  
执行基本登录操作，对接企业 CRM 系统，数据相互独立又可联通。

### 5.2 主要交互

![立项状况](https://github.com/user-attachments/assets/0e09e943-8f22-487b-b0ea-4174f49cb08a)  
根据实际生产销售数据，后端自动计算基于年度、季度、车型、区域、问题复杂度、问题类型、供应商、风险等级、问题频次等多种参数下的产品问题，生成工作任务并自动分配给对应QE。

### 5.3 问题分析

![问题散点图](https://github.com/user-attachments/assets/5646ab8a-6c55-4b33-8a89-4a3c42c01cf4)  
QE 或 SQE 可根据不同的问题，通过数据图形化方式进行快速立项调查、编辑处理相关问题，并自动生成报表，纳入相应的质量管理系统和企业 CRM 母系统。

---

## 6. 主要功能

质量信息系统可实现基于CRM系统数据的定向获取、自动清洗、自动分析、可视化到一键处理的全流程，大幅提升企业质量管理细分垂直领域的工作效率。  

