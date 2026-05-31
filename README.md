# Reddit Beauty Brand Analytics Pipeline

## Overview

This project analyzes beauty-related discussions on Reddit to identify brand mentions, category trends, sentiment patterns, and consumer preferences. The pipeline leverages Databricks and Apache Spark to process large volumes of Reddit posts and comments, transforming unstructured social media data into actionable business insights.

## Objectives

* Extract beauty-related discussions from Reddit.
* Identify beauty brand mentions within posts and comments.
* Categorize brands by product category.
* Analyze brand mention trends over time.
* Measure consumer sentiment toward brands and categories.
* Create dashboards and visualizations for reporting.

## Technology Stack

* Databricks
* Apache Spark (PySpark)
* Python
* SQL
* Delta Lake
* Power BI
* Reddit Data Sources

## Data Pipeline

### 1. Data Ingestion

* Import Reddit posts and comments from source datasets.
* Store raw data in Delta tables.

### 2. Data Cleaning

* Remove duplicates.
* Normalize text formatting.
* Handle missing values.
* Filter non-English and irrelevant content.

### 3. Text Processing

* Split posts into sentences.
* Clean special characters and URLs.
* Standardize brand names.

### 4. Brand Detection

* Match text against predefined beauty brand dictionaries.
* Extract brand mentions from posts and comments.
* Store brand-level observations.

### 5. Category Classification

* Assign brands to beauty categories such as:

  * Makeup
  * Skincare
  * Fragrance
  * Haircare
  * Body Care

### 6. Analytics

* Brand mention frequency
* Top-mentioned brands
* Category popularity
* Monthly and yearly trends
* Sentiment analysis

## Data Model

### Posts Table

| Column       | Description                   |
| ------------ | ----------------------------- |
| post_id      | Unique Reddit post identifier |
| post_content | Reddit post text              |
| created_date | Post creation date            |

### Brand Mentions Table

| Column   | Description                |
| -------- | -------------------------- |
| post_id  | Associated post identifier |
| brand    | Detected beauty brand      |
| category | Beauty category            |

## Sample Metrics

* Total Brand Mentions
* Unique Brands Mentioned
* Top Mentioned Brand
* Mentions by Category
* Mentions Over Time
* Sentiment Distribution

## Dashboard Features

* Brand mention trend analysis
* Category comparison
* Top brands ranking
* Year-over-year growth
* Interactive filtering by category and date

## Key Insights

The solution enables analysts and business stakeholders to:

* Monitor brand visibility on Reddit.
* Identify emerging beauty trends.
* Understand consumer discussions and preferences.
* Compare brand performance across categories.
* Support marketing and product strategy decisions.

## Future Enhancements

* Advanced sentiment analysis using NLP models.
* Topic modeling and trend detection.
* Named Entity Recognition (NER).
* Real-time Reddit data ingestion.
* Automated reporting workflows.

