# University-Recommendation-System-using-Neo4j-and-ML
Choosing the right university can be overwhelming. This project uses Neo4j, a graph database, to build a recommendation system. By analyzing attributes like rankings, type, test scores, and enrollment size through Cypher queries, it provides personalized university suggestions based on student preferences.

## Problem

Students face challenges in identifying universities that align with their aspirations and academic goals. Generic recommendation systems often lack personalization and fail to meet individual preferences.

### Motivating Example

A student interested in medium-sized private universities in New York City with high SAT scores might struggle to find relevant options using traditional systems.

### Research Questions

* How can graph databases improve the accuracy of university recommendations?
* What attributes are most effective in identifying similar universities?
* How can Neo4j enhance personalization in recommendation systems?
  ## Features

* **University Recommendation:** Recommends universities based on user-specified criteria.
* **k-Nearest Neighbors (k-NN):** Employs a k-NN model to find universities similar to the user's preferences.
* **Web API (Flask):** Provides a Flask-based web API for accessing the recommendation system.
* **Data Preprocessing:** Handles data preprocessing, including missing value imputation and feature scaling.

## Tech Stack

* Python
* Flask
* scikit-learn (k-NN, StandardScaler)
* pandas
  
## System Architecture

1.  **Data Loading and Preprocessing:** The university dataset is loaded, and features are selected, missing values are handled, and features are scaled.
2.  **k-NN Model Training:** A k-NN model is trained on the preprocessed data.
3.  **Recommendation Generation:** The `recommend_universities` function uses the trained k-NN model to find the nearest neighbors to a user's preferences, effectively recommending similar universities.
4.  **Flask API:** The Flask API exposes an endpoint (`/recommend`) that accepts user preferences as a JSON payload and returns a JSON list of recommended universities.

## Proposed Approach

The system models universities and their attributes as nodes and relationships in Neo4j. Key attributes include:

* University Name
* City
* Type
* Enrollment Size
* SAT/ACT Scores
* Ranking
* Institutional Control (Public/Private)

The system uses Cypher queries to analyze and recommend universities based on criteria such as:

* Rank and Type: Similar universities within 10 ranks of a reference institution.
* Test Scores: Universities with high SAT/ACT scores.
* Enrollment Size: Institutions with medium-sized enrollments (5,000–10,000 students).
* Institution Type and Location: Private universities in specific cities.
* Top National Universities: Top-ranked institutions.

Graph visualizations in Neo4j enhance understanding by showing connections between universities and attributes.

## Experiment Method

A dataset of universities with attributes like location, SAT/ACT averages, and rankings was imported into Neo4j using the `LOAD CSV` command.  Each query was tested for accuracy and relevance.  Evaluation criteria included:

* Query Performance: Time taken to execute recommendations.
* Recommendation Relevance: How well the recommendations matched user-defined criteria.

## Experiment Outputs

Key findings:

* **Rank-Based Recommendations:** Similar universities to Princeton University were identified effectively.
* **Test Score-Based Recommendations:** Universities with SAT scores >= 1400 or ACT scores >= 30 were listed with rankings.
* **Enrollment-Based Recommendations:** Medium-sized universities were identified efficiently.
* **Specific Criteria Recommendations:** Queries filtered private universities in New York and top national universities.

Graph visualizations provided intuitive insights into how universities relate to one another.

## Conclusion

The Neo4j-based university recommendation system demonstrates the power of graph databases in transforming static, generic recommendations into dynamic, personalized suggestions. By leveraging Cypher queries and graph-based modeling, the system effectively identifies similar universities tailored to user preferences.

## Future Work

Future work will explore integrating machine learning models for further refinement and scalability.
