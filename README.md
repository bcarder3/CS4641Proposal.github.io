# Machine Learning Project Proposal

## 1. Introduction and Background

**The main goal of this project is to predict a song’s genre from features like loudness, tempo, danceability and energy, using both supervised and unsupervised learning.**

### Literature Review

- The first article looks through which supervised learning model classifies a songs genre the most accurately. From the article, Random forest wins at 79.40% accuracy, with decision tree almost tied at 79.30%, Bayes was 77.28%, and k-nearest neighbors was 60.74%. They conclude random forest is the best choice for genre classification on Spotify.

- The second article “presented a paper on how researchers could automatically classify musical genres from audio signals. Claiming that his model worked as well as human classifiers” [2] This article shows how the GTZAN genre dataset became a benchmark for genre data, and argues that its feature-based view of music and genre shaped today’s music technology.

- Another study compared deep learning CNN approach, trained end-to-end, with traditional ML methods that relied on ‘hand-crafted’ time and frequency domain audio features [3].

### Dataset Description

The dataset we will be using is the Spotify track dataset from Kaggle. It contains data from Spotify’s API and includes information for ~114,000 songs. For each song, there is qualitative information such as artist, album, song name, genre, and some quantitative characteristics describing the songs audio features. These characteristics include energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration, musical key, danceability, mode, and a popularity score. For this project we will be focusing on predicting the genre variable.

Dataset Link: [Link](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)

---

## 2. Problem Definition

### Problem

The genre of a song can be hard to classify and is an important part of song recommendations on streaming services. Being able to automate genre classification can help organize large libraries and improve insights. Machine learning provides a way to identify patterns from the audio features, and how that impacts the genre a song will fall into. This can also give insight into how genres differ musically.

---

## 3. Methods

### Data Preprocessing

- Remove duplicate tracks: If a `track_ID` occurs multiple times with different genre labels, we will only keep 1 instance.

- Group together genres: There are 114 unique genres in the dataset. We will group similar genres into one overarching genre.

- Standardize features (using `sklearn.preprocessing.StandardScaler`): Lots of the features are on different scales. We will want to normalize all features so they can be used for the ML models.

### Potential ML Models

- Logistic Regression (supervised): We can use logistic regression to develop a baseline model to predict a song's genre from the features. It will provide a simple starting point for classification and can be used to compare with more complex models. We will use the scikit-learn library and the `sklearn.linear_model.LogisticRegression` class.

- K-Means Clustering (unsupervised): We can use k-means clustering to group songs based on similarities in their audio features. We will use the scikit-learn library and the `sklearn.cluster.KMeans` class.

- Gradient Boosting (supervised): We can use XGBoost to be able to capture complex relationships between the features that are non-linear while also assisting in feature selection regularization, and feature interactions. We will use the XGBoost library and the `xgboost.XGBCClassifier` class.

---

## 4. Potential Results and Discussion

### Evaluation Metrics

- Accuracy (classification): the share of songs assigned the correct genre.
- Macro-F1 (classification): averages the F1 score across genres so each genre counts equally.
- Confusion matrix (classification): shows which genres are most often confused with each other.
- Silhouette score (clustering): how well separated the k-means clusters are.
- Adjusted Rand Index and Normalized Mutual Information (clustering): how closely the clusters match the actual genre labels, from 0 (chance) to 1 (perfect match) [5].

### Project Goals

- Outperform the logistic regression baseline using XGBoost.
- Identify which audio features best distinguish genres.
- Determine whether songs naturally cluster into groups that resemble genres.

### Ethical Considerations

Genre labels reflect Spotify’s categories and may not fairly represent non-Western music. Automated labels could also box artists into categories that affect how their music is recommended.

### Sustainability Considerations

We will compare training time across models and favor lighter models when accuracy is similar.

### Practical Considerations

Spotify has restricted access to audio features in its API, so we will rely on the existing static dataset.

### Expected Results

We expect XGBoost to outperform logistic regression because genre likely depends on nonlinear combinations of audio features. This is supported by prior work, where tree-based models such as random forest achieved the highest accuracy (79.40%) for Spotify genre classification [1]. Accuracy should be much higher on grouped genre families than across all 114 original genres, since similar subgenres are hard to tell apart. For clustering, we expect only partial alignment with genres. Distinct genres like classical or metal should form clear clusters, while similar subgenres overlap, which is consistent with prior findings that genre labels are often noisy and inconsistent [4].

---

## 5. Gantt Chart

[Download the Gantt Chart](GanttChart-1.xlsx)
---

## 6. Contribution Table

| Name | Proposal Contributions |
|---|---|
| Tucker Albaugh | Idea Proposition + Data Sourcing |
| Andrew Wu | Introduction and Background + Gantt Chart |
| Benjamin Carder | Problem Definition + Methods |
| Meeton Kirkuki | Potential Results and Discussion |
| Rida Rehan | Video Generation and Slides |


## 7. References

[1] M. Fiqri, F. B. S. Lizen, and M. Ikrom, “Implementation of supervised learning algorithm on Spotify music genre classification,” *Indones. J. Appl. Technol. Innov. Sci.*, vol. 2, no. 1, pp. 7–12, Feb. 2025, doi: 10.57152/ijatis.v2i1.1102.

[2] A. Jerzak, “An accidental benchmark: The history, contingent power, and lasting traces of the GTZAN dataset,” *Digit. Soc.*, vol. 4, no. 2, Art. no. 34, May 2025, doi: 10.1007/s44206-025-00191-w.

[3] H. Bahuleyan, “Music genre classification using machine learning techniques,” Apr. 2018, *arXiv:1804.01149*.

[4] B. L. Sturm, “The GTZAN dataset: Its contents, its faults, their effects on evaluation, and the future use,” *J. New Music Res.*, vol. 43, no. 2, pp. 147–172, 2014.

[5] L. Hubert and P. Arabie, “Comparing partitions,” *J. Classification*, vol. 2, no. 1, pp. 193–218, 1985.

