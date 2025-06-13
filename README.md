# STQD6324-Assignment3
# 🎬 MovieLens 100k Dataset Analysis Report

![项目封面](images/banner.png)


## 📘 项目简介

本项目基于 [MovieLens 100k 数据集](https://grouplens.org/datasets/movielens/100k/)，使用 Apache Zeppelin 结合 PySpark 和 Spark SQL 进行电影评分数据分析，探索用户偏好、评分分布等行为模式，回答一系列与推荐系统相关的关键问题。

---

## 📂 使用数据集

数据来源于 MovieLens 100k，包括以下三个文件（通过 wget 下载）：

- `u.user`: 用户信息（用户ID, 年龄, 性别, 职业, 邮编）
- `u.data`: 用户评分记录（用户ID, 电影ID, 评分, 时间戳）
- `u.item`: 电影信息（电影ID, 电影名称, 类型标签等）

数据上传至 HDFS `/tmp/ml-100k/` 目录，并通过 Spark 加载。

---

## ⚙️ 技术栈

- Apache Zeppelin
- PySpark（RDD 和 DataFrame）
- Spark SQL
- HDFS 分布式文件系统
- Shell + SQL + Markdown 多段式协作

---

## 🧠 分析目标与问题

本分析任务旨在回答以下五个核心问题：

1. 每部电影的平均评分是多少？
2. 哪些电影的平均评分最高？（排除评分次数少于15次的电影）
3. 哪些活跃用户（评分数 ≥ 50）偏好哪类电影？
4. 哪些用户年龄小于 20 岁？
5. 哪些用户年龄在 30 至 40 岁之间，职业为 scientist？

---

## 📈 分析步骤概览

1. 使用 `%sh` 命令下载并上传原始数据到 HDFS；
2. 使用 `%pyspark` 将数据读取为 RDD，并转换为结构化的 DataFrame；
3. 使用 Spark SQL 注册为临时视图（TempView）以便执行 SQL 查询；
4. 分别编写 SQL 或 PySpark 查询语句完成每个问题的分析；
5. 输出中间结果并生成解释性 Markdown 总结。

---

## 🔍 示例 SQL 查询

计算所有电影的平均评分：

```sql
SELECT movie_id, AVG(rating) AS avg_rating
FROM ratings
GROUP BY movie_id;
