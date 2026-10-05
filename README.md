# Sephora Skincare Recommendation & Satisfaction Analysis

Data science project focused on analyzing skincare product satisfaction, customer reviews, predictive modeling, and personalized product recommendations using Sephora product and review data.

## Project Overview

This project analyzes customer reviews and product information to understand skincare product satisfaction and build recommendation approaches.

The project covers:

- Data auditing and quality checks
- Exploratory data analysis (EDA)
- Customer review text analytics and sentiment analysis
- Skincare concern analysis
- Predictive modeling of product recommendation behavior
- Popularity-based recommendation
- Collaborative filtering
- Content-based recommendation
- Hybrid recommendation
- Recommendation evaluation and coverage analysis

## Dataset

The dataset contains Sephora product information and customer reviews.

The analysis uses:

- `product_info.csv`
- Five customer review CSV files
- Approximately 1.09 million reviews
- 8,494 products in the product catalog
- 2,351 products represented in the review data
- Approximately 503,000 unique reviewers

The raw dataset is not included in this repository because of its size.

## Project Structure

```text
sephora-skincare-recommendation/
│
├── data/
│   └── README.md
│
├── notebooks/
│   ├── 01_data_audit.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_text_analytics.ipynb
│   ├── 04_predictive_modeling.ipynb
│   ├── 05_recommender_system.ipynb
│   └── README.md
│
├── results/
│   ├── figures/
│   │   └── README.md
│   └── tables/
│       └── README.md
│
├── src/
│   └── README.md
│
├── requirements.txt
└── README.md
```


Analysis Workflow
1. Data Audit
The first notebook examines:
- Dataset dimensions
- Data types
- Missing values
- Duplicate records
- Rating distributions
- Recommendation labels
- Reviewer activity
- Product review counts
- Product and reviewer coverage
2. Exploratory Data Analysis
The EDA examines:
- Product categories
- Skincare products
- Price distributions
- Ratings
- Review volume
- Recommendation rates
- Skin type
- Skin tone
- Brand and product popularity
- Relationships between price, reviews, and ratings
3. Text Analytics
Customer reviews were cleaned and analyzed using NLP techniques.
The analysis includes:
- Text cleaning
- Stopword removal
- Review length analysis
- Common word analysis
- TF-IDF
- VADER sentiment analysis
- Skincare concern keyword analysis
Major skincare concerns identified include:
- Dryness
- Redness
- Oiliness
- Acne
- Sensitivity
- Texture
- Aging
- Pores
- Dark spots
- Dullness
4. Predictive Modeling
Several models were compared for predicting the is_recommended outcome:
- Logistic Regression
- Random Forest
- XGBoost
The models achieved high predictive performance, but rating was found to be an extremely strong predictor of recommendation behavior. Therefore, the results are interpreted carefully because some variables are closely related to the target and may not represent true pre-purchase recommendation prediction.
5. Recommendation System
Four recommendation approaches were explored:
Popularity Baseline
Uses review volume and average rating to identify popular products.
Collaborative Filtering
Uses user-product interaction patterns to identify products associated with similar user behavior.
The interaction matrix is highly sparse, with many users having only one product interaction. A leakage-controlled evaluation produced:
- Precision@10: 0.00
- Recall@10: 0.00
- Hit Rate@10: 0.00
- Catalog Coverage@10: 50%
These results highlight the limitations of collaborative filtering in a sparse dataset.
Content-Based Recommendation
Uses product metadata such as:
- Product name
- Brand
- Category
- Secondary category
- Tertiary category
TF-IDF and cosine similarity are used to identify similar products.
Hybrid Recommendation
Combines:
- Content similarity
- Collaborative filtering
- Popularity
The hybrid system provides a practical way to combine product characteristics, interaction signals, and product popularity.
Example Recommendation
For the LANEIGE Lip Sleeping Mask, the hybrid recommender identified related products including:
- LANEIGE Lip Glowy Balm
- SEPHORA COLLECTION Lip Sleeping Mask
- LANEIGE Lip Treatment Balm
- fresh Sugar Advanced Lip Balm
- fresh Sugar Hydrating Lip Balm
- Tatcha The Kissu Lip Mask
Key Findings
Some important findings from the project include:
- Customer ratings are strongly concentrated toward higher ratings, with 5-star reviews making up the largest share.
- Skin type representation is uneven, with combination skin being the most common recorded type.
- Reviewers often have very few interactions, creating a major cold-start and sparsity challenge for collaborative filtering.
- Price showed very little relationship with product rating in the analyzed data.
- Review text frequently focuses on skin, product experience, usage, dryness, moisturizers, and other skincare-related terms.
- Sentiment generally increases with product rating.
- Dryness, redness, oiliness, acne, and sensitivity were among the most frequently identified skincare concerns.
- Content-based recommendation provides useful support for products with limited interaction history.
- The hybrid approach combines multiple recommendation signals and provides a practical prototype for personalized skincare recommendations.
Limitations
The project has several limitations:
- The dataset contains substantial rating and recommendation imbalance.
- Many users have only one recorded product interaction.
- Collaborative filtering is affected by high user-item sparsity.
- The predictive model uses rating as a strong predictor of recommendation behavior, limiting its interpretation as a true pre-purchase prediction model.
- The current recommender is a prototype and would require further user-level evaluation before deployment.
- Skin type and other demographic/profile fields contain missing values and uneven representation.
- The current offline collaborative filtering evaluation produced weak retrieval performance.
Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- NLTK
- VADER Sentiment
- XGBoost
- SciPy
- Google Colab
- GitHub
Project Timeline
The project follows a six-week internship-style workflow:
1. Research and project planning
2. Data audit, cleaning, and EDA
3. Text analytics and customer segmentation
4. Predictive modeling and explainability
5. Recommender system development and evaluation
6. Business recommendations, documentation, and final presentation
Future Improvements
Possible future improvements include:
- More advanced personalized recommendation models
- Better cold-start handling
- More rigorous ranking evaluation using NDCG@K
- Improved user-level personalization
- Fairness and representation analysis
- Ingredient-based recommendation
- Interactive recommendation dashboard
- More robust hybrid model evaluation
Author
Data Science Internship Project — Yuva Intern
