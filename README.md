# Machine Learning Project Proposal

## 1. Introduction and Background

The main goal of this project is to predict a song’s genre from features like loudness, tempo, danceability, and energy using both supervised and unsupervised learning.

### Literature Review

- The first article examines which supervised learning model classifies a song's genre most accurately. Random Forest achieved the highest accuracy at **79.40%**, followed closely by Decision Tree at **79.30%**, Bayes at **77.28%**, and K-Nearest Neighbors at **60.74%**. The study concluded that Random Forest was the strongest model for genre classification on Spotify data [1].

- The second article discusses research on automatically classifying musical genres from audio signals and how the GTZAN genre dataset became a major benchmark for music genre classification. It also explains how the dataset's feature-based view of music and genre influenced later music technology research [2].

- Another study compared a deep learning CNN approach, trained end-to-end, with traditional machine learning methods that relied on hand-crafted time- and frequency-domain audio features [3].

### Dataset Description

The dataset we will be using is the **Spotify Tracks Dataset** from Kaggle. It contains data from Spotify's API and includes information for approximately **114,000 songs**.

For each song, the dataset contains qualitative information such as:

- Artist
- Album
- Song name
- Genre

It also contains quantitative audio characteristics such as:

- Energy
- Loudness
- Speechiness
- Acousticness
- Instrumentalness
- Liveness
- Valence
- Tempo
- Duration
- Musical key
- Danceability
- Mode
- Popularity score

For this project, we will focus on predicting the **genre** variable.

**Dataset Link:** [Spotify Tracks Dataset](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)

---

## 2. Problem Definition

### Problem and Motivation

- The genre of a song can be difficult to classify and is an important component of music recommendation systems on streaming platforms.

- Automating genre classification can help organize large music libraries and potentially improve recommendation systems.

- Machine learning provides a way to identify patterns across audio features and determine how those characteristics relate to the genre of a song.

- This analysis can also provide insight into how different genres differ musically based on measurable audio characteristics.

---

## 3. Methods

### Data Preprocessing

- **Remove duplicate tracks:** If a `track_id` occurs multiple times with different genre labels, we will keep only one instance.

- **Group similar genres:** There are 114 unique genres in the dataset. We will group similar genres into broader genre categories to make classification more manageable and interpretable.

- **Standardize features:** We will use `sklearn.preprocessing.StandardScaler` because many of the audio features are measured on different scales. Standardization will place the numerical features on comparable scales before they are used in the machine learning models.

### Potential Machine Learning Models

#### Logistic Regression — Supervised

- Logistic Regression will be used as a baseline model to predict a song's genre from its audio features.
- It will provide a simple starting point for classification and allow us to compare its performance with more complex models.
- We will use the `sklearn.linear_model.LogisticRegression` class from scikit-learn.

#### K-Means Clustering — Unsupervised

- K-Means will be used to group songs based on similarities in their audio features without using the genre labels during training.
- We can then compare the resulting clusters with the actual genre labels to determine whether songs naturally form groups that resemble genres.
- We will use the `sklearn.cluster.KMeans` class from scikit-learn.

#### Gradient Boosting — Supervised

- We will use XGBoost to capture complex and nonlinear relationships between audio features.
- XGBoost can also capture interactions between features and includes regularization techniques that can help reduce overfitting.
- We will use the `xgboost.XGBClassifier` class from the XGBoost library.

---

## 4. Potential Results and Discussion

### Evaluation Metrics

We will use quantitative metrics to evaluate the performance of our models.

- **Accuracy:** Measures the overall percentage of songs whose genres are classified correctly.

- **Precision:** Measures how often songs predicted to belong to a specific genre actually belong to that genre.

- **Recall:** Measures how many songs from each actual genre are correctly identified.

- **F1-Score:** Balances precision and recall and is useful when genre classes are not evenly represented.

- **Silhouette Score:** Measures how well songs fit within their assigned clusters and how separated the clusters are from one another.

- **Adjusted Rand Index (ARI) and Normalized Mutual Information (NMI):** Measure how closely the clusters produced by K-Means correspond with the actual genre labels [4].

### Project Goals

- Outperform the Logistic Regression baseline using a more advanced supervised learning model.
- Identify which audio features have the strongest relationship with song genre.
- Determine whether songs naturally cluster into groups that resemble known genres.

### Ethical Considerations

Genre labels are not always objective and may reflect Spotify's existing categorization system. Some songs may belong to multiple genres, and broad genre labels may fail to accurately represent niche, hybrid, or non-Western music styles. Because of this, model predictions should not be treated as absolute definitions of a song's genre.

### Sustainability Considerations

We will compare model complexity and training time across different methods. If two models produce similar classification performance, we will favor the model that requires less computational power and training time.

### Practical Considerations

Spotify has restricted access to some audio features through its API, so this project will rely on the existing static Kaggle dataset rather than collecting new data directly from Spotify.

### Expected Results

We expect more complex models such as XGBoost to outperform Logistic Regression because genre may depend on nonlinear combinations of several audio features. We also expect K-Means clustering to show partial alignment with actual genre labels. Genres with very different acoustic characteristics may form clearer clusters, while closely related subgenres may overlap. This would suggest that genre is influenced by measurable audio characteristics but is not determined by audio features alone [5], [6].

---

## 5. Gantt Chart

| Task | Member(s) Responsible | Timeline |
|---|---|---|
| Task 1 |  |  |
| Task 2 |  |  |
| Task 3 |  |  |
| Task 4 |  |  |
| Task 5 |  |  |

---

## 6. Contribution Table

| Name | Proposal Contributions |
|---|---|
| Tucker Albaugh | Idea Proposition + Data Sourcing |
| Andrew Wu | Introduction and Background + Gantt Chart |
| Benjamin Carder | Problem Definition + Methods |
| Meeton Kirkuki | Potential Results and Discussion |
| Rida Rehan | Video Generation and Slides |


## 6. References

[1] M. Fiqri, F. B. S. Lizen, and M. Ikrom, "Implementation of supervised learning algorithm on Spotify music genre classification," *Indones. J. Appl. Technol. Innov. Sci.*, vol. 2, no. 1, pp. 7–12, Feb. 2025, doi: 10.57152/ijatis.v2i1.1102.

[2] A. Jerzak, "An accidental benchmark: The history, contingent power, and lasting traces of the GTZAN dataset," *Digit. Soc.*, vol. 4, no. 2, Art. no. 34, May 2025, doi: 10.1007/s44206-025-00191-w.

[3] H. Bahuleyan, "Music genre classification using machine learning techniques," *arXiv:1804.01149*, Apr. 2018.

[4] L. Hubert and P. Arabie, "Comparing partitions," *J. Classification*, vol. 2, no. 1, pp. 193–218, 1985.

[5] M. Interiano, K. Kazemi, L. Wang, J. Yang, Z. Yu, and N. L. Komarova, "Musical trends and predictability of success in contemporary songs in and out of the top charts," *R. Soc. Open Sci.*, vol. 5, no. 5, Art. no. 171274, 2018.

[6] B. L. Sturm, "The GTZAN dataset: Its contents, its faults, their effects on evaluation, and the future use," *J. New Music Res.*, vol. 43, no. 2, pp. 147–172, 2014.


