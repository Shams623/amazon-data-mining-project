# 🛒 E-Commerce Recommendation System – Amazon Data Mining Project

## 📌 Project Overview

This project applies data mining and machine learning techniques on an Amazon e-commerce dataset to build an intelligent product recommendation system.

The main goal is to analyze customer-product interactions, discover product relationships, rank important products, and use sentiment analysis to improve recommendation quality.

## 📂 Dataset

The project uses the `amazon.csv` dataset, which contains product information, categories, ratings, prices, users, and customer reviews.

### Dataset Information

- Rows: 1,463 after cleaning
- Columns: 18 after preprocessing
- Unique Products: 1,349
- Unique Users: 1,194
- Main fields used:
  - Product ID
  - Product Name
  - Category
  - Rating
  - Review Content
  - User ID
  - Actual Price
  - Discounted Price

## 🎯 Project Objectives

- Clean and preprocess Amazon product data
- Build user-product transaction baskets
- Apply Association Rule Mining using Apriori
- Generate product recommendation rules
- Build a product co-purchase network
- Apply PageRank to identify important products
- Perform BERT-based sentiment analysis on customer reviews
- Visualize frequent products, association rules, PageRank results, and sentiment distribution

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- NetworkX
- Mlxtend
- Transformers
- Hugging Face
- Jupyter Notebook

## 🧹 Data Preprocessing

The dataset was cleaned and prepared through the following steps:

- Removed rows with missing critical values
- Converted price columns from text format to numeric values
- Converted discount percentage into numeric format
- Extracted the main product category
- Shortened product names for better visualization
- Split pipe-separated user IDs into separate user-product interactions
- Built transaction baskets for users who reviewed more than one product

## 🔍 Association Rule Mining

Association Rule Mining was applied using the Apriori algorithm to discover relationships between products.

### Parameters Used

- Minimum support: 0.005
- Minimum confidence: 0.30
- Minimum lift: 1.0
- Maximum itemset length: 3

### Results

- Frequent itemsets found: 811
- Association rules generated: 2,090
- 1-itemsets: 262
- 2-itemsets: 301
- 3-itemsets: 248

This helps identify products that are frequently reviewed or purchased together.

## 🕸️ PageRank Product Network

A product co-purchase network was created using NetworkX.

In this graph:

- Nodes represent products
- Edges represent co-purchase relationships
- Edge weights represent how often products appear together

PageRank was then applied to identify the most important products in the recommendation network.

### PageRank Results

- Graph nodes: 262
- Graph edges: 328
- Top PageRank product: Nokia 105 Plus Single SIM Keypad Mobile Phone
- PageRank score: 0.004391

PageRank helps recommend products that are not only popular, but also connected to other important products.

## 🤖 BERT-Based Sentiment Analysis

Customer reviews were analyzed using a pre-trained sentiment analysis model from Hugging Face.

### Model Used

`cardiffnlp/twitter-roberta-base-sentiment-latest`

The model classifies reviews into:

- Positive
- Neutral
- Negative

### Sentiment Analysis Results

A sample of 300 reviews was analyzed.

| Sentiment | Count | Percentage |
|----------|-------|------------|
| Positive | 215 | 71.7% |
| Neutral | 41 | 13.7% |
| Negative | 44 | 14.7% |

Average confidence score: 0.7733

## 📊 Visualizations

The project includes several visualizations:

- Top frequent products bar chart
- Association rule graph
- PageRank product network
- PageRank ranking chart
- BERT sentiment distribution chart
- Sentiment distribution by product category

## 💡 How Sentiment Improves Recommendations

Sentiment analysis improves the recommendation system by adding a quality-based filter.

Instead of recommending products only because they are frequently bought together, the system can also consider customer satisfaction.

A possible recommendation score can be:

```text
recommendation_score = lift × confidence × sentiment_positivity_ratio