# Predicting Product Satisfaction and Improving Personalized Skincare Recommendations

## 1. Project Overview

This project focuses on analyzing customer reviews and product information to understand skincare product satisfaction, predict recommendation behavior, and explore personalized skincare recommendation approaches.

The project uses Sephora product and customer review data to combine exploratory data analysis, natural language processing, machine learning, and recommender system techniques.

The main goal is to understand what factors are associated with customer satisfaction and to compare different approaches for recommending skincare products.

---

## 2. Project Objectives

The main objectives of this project are:

- Analyze Sephora product and customer review data.
- Understand customer satisfaction and recommendation behavior.
- Explore relationships between ratings, product characteristics, and customer profiles.
- Analyze review text using natural language processing.
- Identify common skincare concerns discussed by customers.
- Predict whether a customer recommends a product.
- Compare multiple machine learning models.
- Build and compare popularity-based, collaborative filtering, content-based, and hybrid recommendation approaches.
- Evaluate recommendation performance using ranking and coverage metrics.
- Identify limitations such as data sparsity, cold-start problems, and representation bias.

---

## 3. Dataset

The project uses the Sephora Products and Skincare Reviews dataset.

### Product Dataset

The product dataset contains:

- 8,494 products
- 27 product-related columns

The product catalog contains categories such as:

- Skincare
- Makeup
- Hair
- Fragrance
- Bath & Body
- Mini Size
- Men
- Tools & Brushes
- Gifts

There are 2,420 skincare products in the full product catalog.

### Review Dataset

The review data contains:

- 1,094,411 customer reviews
- 2,351 products with reviews
- Approximately 503,000 unique reviewers

The review data includes information such as:

- Rating
- Recommendation status
- Review text
- Review title
- Skin type
- Skin tone
- Eye color
- Hair color
- Helpfulness
- Product information
- Brand information
- Price

---

## 4. Project Workflow

The project follows the workflow below:

```text
Data Collection
      ↓
Data Audit & Cleaning
      ↓
Exploratory Data Analysis
      ↓
Text Analytics & NLP
      ↓
Predictive Modeling
      ↓
Recommendation Systems
      ↓
Model Evaluation
      ↓
Business Insights & Future Improvements
```

---

## 5. Methodology

### 5.1 Data Audit and Cleaning

The first stage focused on understanding the structure and quality of the dataset.

The following checks were performed:

- Dataset dimensions
- Column names and data types
- Missing values
- Duplicate records
- Rating distributions
- Recommendation distributions
- Unique products
- Unique reviewers
- Reviewer activity
- Product review counts
- Category distributions

Special attention was given to missing customer profile information and recommendation values.

Missing recommendation values were not automatically treated as negative recommendations.

---

### 5.2 Exploratory Data Analysis

The exploratory analysis examined:

- Product category distributions
- Skincare product prices
- Product ratings
- Review volume
- Recommendation rates
- Customer skin types
- Skin tones
- Helpfulness
- Review text length
- Top brands
- Top products
- Common review titles
- Relationships between price and rating
- Relationships between review volume and rating
- Recommendation rates by skin type
- Recommendation rates by rating
- Customer profile characteristics

For skincare products, the average price was approximately $60.51 and the median price was approximately $44.

The average rating among reviewed skincare products was approximately 4.23.

The correlation between price and rating was very small, indicating little linear relationship between product price and average rating in this dataset.

---

### 5.3 Text Analytics and NLP

Customer review text was analyzed to identify common themes and sentiment.

The text preprocessing process included:

- Converting text to lowercase
- Removing URLs
- Normalizing whitespace
- Removing unnecessary punctuation
- Handling short or empty reviews
- Removing stopwords for frequency analysis
- Handling common contractions

After preprocessing, 1,092,931 reviews were available for NLP analysis.

VADER sentiment analysis was used to classify reviews into:

- Positive
- Neutral
- Negative

The sentiment distribution was:

| Sentiment | Reviews | Percentage |
|---|---:|---:|
| Positive | 986,496 | 90.26% |
| Negative | 72,693 | 6.65% |
| Neutral | 33,742 | 3.09% |

Sentiment generally increased with product rating.

Mean sentiment by rating:

| Rating | Mean Sentiment |
|---:|---:|
| 1 | 0.168 |
| 2 | 0.402 |
| 3 | 0.563 |
| 4 | 0.726 |
| 5 | 0.747 |

TF-IDF was also used to identify important terms and phrases in customer reviews.

Some of the most common terms included:

- skin
- product
- love
- use
- like
- face
- using
- really
- great
- dry
- moisturizer
- makeup
- cream
- recommend

---

### 5.4 Skincare Concern Analysis

Customer reviews were also analyzed for common skincare concerns.

Keyword-based concern categories included:

- Dryness
- Acne
- Oiliness
- Redness
- Sensitivity
- Aging
- Dark Spots
- Pores
- Dullness
- Texture

The most frequently detected concerns were:

| Concern | Reviews | Percentage |
|---|---:|---:|
| Dryness | 225,073 | 20.59% |
| Redness | 189,442 | 17.33% |
| Oiliness | 178,639 | 16.34% |
| Acne | 146,260 | 13.38% |
| Sensitivity | 137,704 | 12.60% |
| Texture | 136,888 | 12.52% |
| Aging | 99,880 | 9.14% |
| Pores | 64,632 | 5.91% |
| Dark Spots | 24,834 | 2.27% |
| Dullness | 23,489 | 2.15% |

These categories overlap because a single review can mention multiple skincare concerns.

---

## 6. Predictive Modeling

The predictive modeling task focused on predicting whether a customer recommended a product.

Only reviews with a known recommendation value were used for the modeling task.

The final modeling dataset contained 926,423 reviews.

### Features

The baseline model used:

- Rating
- Price
- Skin type

Additional experiments considered:

- Helpfulness
- Total feedback count
- Positive feedback count
- Negative feedback count

Categorical skin-type values were converted using one-hot encoding.

---

## 7. Model Comparison

Three machine learning models were compared:

- Logistic Regression
- Random Forest
- XGBoost

### Results

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 96.36% | 99.13% | 96.51% | 97.80% | 98.52% |
| Random Forest | 96.32% | 99.01% | 96.58% | 97.78% | 98.47% |
| XGBoost | 96.35% | 99.11% | 96.53% | 97.80% | 98.57% |

The three models performed very similarly.

XGBoost achieved the highest ROC-AUC, while Logistic Regression provided a highly competitive and more interpretable baseline.

### Important Modeling Limitation

Rating is strongly associated with whether a customer recommends a product.

Therefore, the high predictive performance should not be interpreted as proof that the model can accurately predict recommendations before a customer experiences a product.

Some feedback-related variables may also introduce information that would not be available before the review is written.

This is an important limitation of the predictive modeling stage.

---

## 8. Recommendation Systems

Several recommendation approaches were explored.

### 8.1 Popularity-Based Recommendation

The popularity baseline ranked products using review volume and average rating.

This provides a simple non-personalized benchmark.

The most reviewed products included products such as:

- LANEIGE Lip Sleeping Mask
- fresh Soy Hydrating Gentle Face Cleanser
- Josie Maran 100 percent Pure Argan Oil
- First Aid Beauty Ultra Repair Cream
- Dr. Dennis Gross Alpha Beta Extra Strength Daily Peel Pads

The popularity approach is useful for recommending products that are already widely reviewed and popular.

However, it does not personalize recommendations for individual users.

---

### 8.2 Collaborative Filtering

Collaborative filtering was implemented using user-product interactions.

Users with at least two product interactions were used for the collaborative filtering preparation.

The resulting interaction data contained:

- 209,105 active users
- 2,330 products
- Approximately 99.84% sparsity

This high sparsity is a major challenge because most users reviewed only a very small number of products.

Approximately 294,111 users had interacted with only one product.

---

### 8.3 Collaborative Filtering Evaluation

A leakage-controlled evaluation was performed using a train/test setup.

The final evaluation results were:

| Metric | Result |
|---|---:|
| Precision@10 | 0.00 |
| Recall@10 | 0.00 |
| Hit Rate@10 | 0.00 |
| Coverage@10 | 50.00% |

The collaborative filtering baseline did not successfully retrieve the held-out positive product in the evaluation sample.

However, it was able to recommend products covering approximately 50% of the available product catalog.

This result highlights the difficulty of collaborative filtering with extremely sparse user-product interactions.

---

### 8.4 Content-Based Recommendation

A content-based recommendation approach was developed using product metadata.

The product representation included:

- Product name
- Brand
- Primary category
- Secondary category
- Tertiary category

TF-IDF was used to represent product metadata and cosine similarity was used to identify similar products.

For example, recommendations for the LANEIGE Lip Sleeping Mask included other lip masks, lip balms, and related skincare products.

This approach is useful for recommending products with similar characteristics and can support cold-start situations where user interaction data is unavailable.

---

### 8.5 Hybrid Recommendation

A hybrid recommendation approach was also developed by combining:

- Content similarity
- Collaborative filtering similarity
- Popularity

The prototype used the following weights:

```text
Content similarity       60%
Collaborative filtering 30%
Popularity               10%
```

For a sample product such as the LANEIGE Lip Sleeping Mask, the hybrid system generated recommendations including:

1. LANEIGE Lip Glowy Balm
2. Sephora Collection Lip Sleeping Mask
3. LANEIGE Lip Treatment Balm
4. Sephora Collection Lip Sleeping Mask
5. fresh Sugar Advanced Lip Balm
6. fresh Sugar Hydrating Lip Balm
7. Tatcha The Kissu Lip Mask
8. LANEIGE Cica Sleeping Mask
9. Farmacy Honey Butter Beeswax Lip Balm
10. LANEIGE BTS Lip Sleeping Mask

The hybrid approach demonstrates how different recommendation signals can be combined.

However, the current hybrid implementation is a product-to-product recommendation prototype rather than a fully personalized user-level recommender.

A strict leakage-controlled evaluation of the hybrid system has not yet been completed.

---

## 9. Recommendation Method Comparison

| Method | Personalization | Main Signal | Cold-Start Support |
|---|---|---|---|
| Popularity Baseline | No | Review volume + rating | Good for popular products |
| Collaborative Filtering | Yes | User-product interactions | Weak |
| Content-Based | No | Product metadata | Strong |
| Hybrid | Partial | Content + CF + popularity | Strong |

---

## 10. Key Findings

Several important findings emerged from the analysis:

### Customer Satisfaction

- Most reviews were positive.
- 5-star reviews represented approximately 63.87% of all reviews.
- Approximately 71.10% of all reviews explicitly recommended the product.
- Recommendation values were missing for approximately 15.35% of reviews.

### Customer Behavior

- The median number of reviews per customer was 1.
- A large proportion of users interacted with only one product.
- This creates a major challenge for collaborative filtering.

### Product Ratings

- The average rating among reviewed skincare products was approximately 4.23.
- Price showed almost no linear correlation with product rating.
- Review volume also showed only a weak relationship with rating.

### Review Text

Common review terms focused heavily on:

- Skin
- Product
- Face
- Moisturizer
- Dryness
- Makeup
- Cream
- Usage experience

### Skincare Concerns

Dryness, redness, oiliness, acne, sensitivity, and texture were among the most frequently detected concerns.

### Machine Learning

The predictive models achieved approximately 96% accuracy, but the strong performance is largely influenced by the use of rating as a predictor of recommendation behavior.

### Recommendation Systems

The main challenge for collaborative filtering was extreme data sparsity.

The leakage-controlled collaborative filtering evaluation produced zero Precision@10 and Recall@10, demonstrating that a simple collaborative filtering approach is not sufficient for this dataset.

---

## 11. Limitations

The project has several limitations:

- The dataset contains strong rating imbalance.
- Many users have only one product interaction.
- User-product interactions are highly sparse.
- Recommendation values contain missing observations.
- Customer demographic/profile fields are incomplete.
- Keyword-based skincare concern detection may miss context and synonyms.
- VADER sentiment analysis may not capture all skincare-specific language.
- Rating is strongly associated with the recommendation target in the predictive model.
- The current content-based model relies mainly on product metadata.
- The hybrid recommender is currently a prototype and is not yet fully personalized.
- The hybrid recommender has not yet been evaluated using the same leakage-controlled protocol as collaborative filtering.
- Fairness and representation issues may exist because skin type and skin tone groups are not equally represented.

---

## 12. Project Structure

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
├── src/
│   └── README.md
│
├── results/
│   ├── figures/
│   │   └── README.md
│   │
│   └── tables/
│       └── README.md
│
├── requirements.txt
└── README.md
```

---

## 13. Notebooks

### Notebook 1 — Data Audit

`01_data_audit.ipynb`

Covers:

- Dataset loading
- Dataset dimensions
- Column inspection
- Missing values
- Duplicate checks
- Rating distribution
- Recommendation distribution
- Reviewer activity
- Product review counts

### Notebook 2 — Exploratory Data Analysis

`02_eda.ipynb`

Covers:

- Product categories
- Skincare products
- Price analysis
- Rating analysis
- Review volume
- Recommendation behavior
- Customer profile analysis
- Brand and product analysis
- Correlation analysis
- Review text characteristics

### Notebook 3 — Text Analytics

`03_text_analytics.ipynb`

Covers:

- Text cleaning
- Stopword removal
- Word frequency analysis
- VADER sentiment analysis
- TF-IDF
- Skincare concern detection

### Notebook 4 — Predictive Modeling

`04_predictive_modeling.ipynb`

Covers:

- Target preparation
- Feature engineering
- Train/test split
- Logistic Regression
- Random Forest
- XGBoost
- Model comparison
- Confusion matrix
- Feature importance

### Notebook 5 — Recommender System

`05_recommender_system.ipynb`

Covers:

- User-product interactions
- Popularity baseline
- Collaborative filtering
- Sparsity analysis
- Content-based recommendation
- Hybrid recommendation
- Recommendation evaluation
- Recommendation comparison

---

## 14. Technologies Used

### Programming

- Python
- Google Colab
- Jupyter Notebook

### Data Analysis

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn

### Natural Language Processing

- NLTK
- VADER
- Scikit-learn TF-IDF

### Machine Learning

- Scikit-learn
- XGBoost

### Recommender Systems

- Cosine similarity
- TF-IDF
- Collaborative filtering
- Content-based recommendation
- Hybrid recommendation

### Data Storage

- CSV
- GitHub

---

## 15. Installation

Clone the repository and install the required Python packages:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY-NAME.git
cd YOUR-REPOSITORY-NAME
pip install -r requirements.txt
```

The notebooks can then be opened using Jupyter Notebook or Google Colab.

---

## 16. Usage

The recommended workflow is to run the notebooks in the following order:

```text
01_data_audit.ipynb
        ↓
02_eda.ipynb
        ↓
03_text_analytics.ipynb
        ↓
04_predictive_modeling.ipynb
        ↓
05_recommender_system.ipynb
```

Each notebook focuses on a different stage of the project.

The original Sephora dataset is not stored directly in this repository because of its size.

---

## 17. Future Improvements

Future development could include:

- More advanced collaborative filtering algorithms.
- Matrix factorization.
- Neural recommendation models.
- Better cold-start strategies.
- Ingredient-level product similarity.
- Skin-concern-based recommendation.
- More rigorous user-level recommendation evaluation.
- NDCG@K and additional ranking metrics.
- Recommendation coverage analysis.
- Fairness analysis across skin types and skin tones.
- Personalized recommendations using individual user histories.
- Dashboard development for business users.
- Explainable recommendations showing why a product was recommended.

---

## 18. Project Timeline

The project follows a six-week development plan:

### Week 1
Research, problem definition, and dataset understanding.

### Week 2
Data audit, cleaning, and exploratory data analysis.

### Week 3
Text analytics, sentiment analysis, and customer segmentation.

### Week 4
Predictive modeling and explainability.

### Week 5
Recommendation system development and evaluation.

### Week 6
Business recommendations, dashboard development, and final project presentation.

---

## 19. Conclusion

This project combines data analysis, natural language processing, machine learning, and recommender systems to study skincare customer satisfaction and recommendation behavior.

The analysis shows that customer reviews contain useful information about product satisfaction and skincare concerns.

The predictive models achieved strong performance, although the results must be interpreted carefully because rating is closely related to recommendation behavior.

The recommendation experiments also demonstrate the challenges of building personalized systems from sparse customer-product interactions.

The hybrid approach provides a useful direction for combining product similarity, collaborative signals, and popularity, while future work can focus on stronger personalization, cold-start handling, fairness, and more rigorous recommendation evaluation.

---

## 20. Author

**Yuva Intern**

Data Science Internship Project

Project: Predicting Product Satisfaction and Improving Personalized Skincare Recommendations
```
Ananthapadmanabhan
sephora-skincare-recommendation
```

