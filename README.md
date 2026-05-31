# 💄 Reddit Beauty Brand Analytics Pipeline

##  Overview
This project analyzes beauty-related discussions on Reddit to identify brand mentions, category trends, sentiment patterns, and consumer preferences. Using **Databricks** and **Apache Spark**, the pipeline processes raw Reddit posts and comments, transforms unstructured text into structured datasets, and exports the data to enable visualization dashboards in **Power BI**.

---

##  Objectives
* **Data Collection:** Ingest beauty-related discussions from Reddit subreddit r/beautytalkph using the official Reddit API.
* **Scalable Processing:** Store and process massive volumes of posts and comments in Databricks using Apache Spark.
* **Entity Extraction:** Automatically identify beauty brands, product categories, and social media platforms from unstructured text.
* **Data Transformation:** Normalize and transform unstructured text into structured, sentence-level analytical datasets.
* **Business Intelligence:** Build an interactive Power BI dashboard for visualization of data.


---

##  Technology Stack
* **Data Ingestion:** Python, Reddit API (PRAW)
* **Processing & Compute:** Databricks, Apache Spark (PySpark)
* **Storage & Management:** Delta Lake, Spark SQL
* **Visualization:** Power BI

---

## 🔄 Data Pipeline Architecture

### 1. Data Ingestion
Data is extracted from the `r/beautytalkph` subreddit via the Reddit API (PRAW) and ingested directly into two raw Delta Lake tables:

* **Posts Table:** `post_id`, `post_content`, `created_date`, `number_of_comments`, `number_of_upvotes`
* **Comments Table:** `comment_id`, `post_id`, `comment_body`, `created_date`, `comment_upvotes`

### 2. Entity Detection & NLP
* **Brand & Category Mapping:** Scans text for brand names and product categories using predefined lookup dictionaries.
* **Platform Tracking:** Detects mentions of other social media networks (e.g., TikTok, Instagram).
* **Sentiment Analysis:** Performs sentence-level sentiment classification to evaluate consumer perception (Positive, Neutral, Negative).

### 3. Data Transformation & Normalization
To prevent analytical bias and handle multi-entity text, the unstructured data undergoes the following transformations:
1.  **Tokenization:** Splits long posts and comments into individual sentences.
2.  **Explode Operations:** Explodes arrays of detected brands, categories, and platforms into separate rows to normalize the data (1 mention per row).

### 4. Analytics & Aggregations
The final data is used to analyze:
* **Top Mentioned Brands, Categories, and Platforms:** See which ones get talked about the most.
* **Yearly Trends:** Track how mentions change over the years.
* **Sentiment Analysis:** See if people are saying positive, neutral, or negative things about specific brands, categories, or platforms.

---
### Table Schemas

#### 1. Posts Table
| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `post_id` | `STRING` (PK) | Unique Reddit post identifier |
| `post_content`| `STRING` | Raw text body of the post |
| `created_date`| `TIMESTAMP` | Date and time the post was created |
| `number_of_comments` | `INT` | Total comment count |
| `number_of_upvotes` | `INT` | Total upvote count |

#### 2. Comments Table
| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `comment_id` | `STRING` (PK) | Unique Reddit comment identifier |
| `post_id` | `STRING` (FK) | Reference to the parent post identifier |
| `comment_body`| `STRING` | Raw text body of the comment |
| `created_date`| `TIMESTAMP` | Date and time the comment was created |
| `comment_upvotes` | `INT` | Total comment upvote count |

#### 3. Sentence-Level Table (Analytical Output)
| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `sentence` | `STRING` | The extracted individual sentence text |
| `post_id` | `STRING` (FK) | Source post identifier |
| `comment_id` | `STRING` (FK) | Source comment identifier (NULL if from a post) |
| `brand_found` | `STRING` | Detected beauty brand name |
| `category_mentioned` | `STRING` | Detected product category (e.g., Skincare, Makeup) |
| `platform_mentioned` | `STRING` | Detected social media platforms (e.g., TikTok) |
| `sentiment` | `STRING` / `FLOAT` | Sentiment classification label |
| `date` | `DATE` |  Date and time the post was created |

---

## 📊 Power BI Dashboard

<img width="1054" height="819" alt="image" src="https://github.com/user-attachments/assets/b2d6cd63-5e84-4c05-91f0-3eaa70e620ef" />
