# Decoding Popularity - A competitve Analysis of Taylor Swift and BTS on Spotify
# Problem Definition
How do the musical characteristics of Taylor Swift and BTS on Spotify differ, and what insights can these differences provide into their respective popularity and audience preferences? 

Our objective is to dissect the musical attributes of songs by Taylor Swift and BTS on Spotify, discerning the distinguishing features between them. We aim to correlate these characteristics with their respective popularity, providing insights into audience preferences. This will involve a detailed comparative analysis of song features, and the application of machine learning techniques to understand the influence of these features on audience listening habits.

# What our insights link to the Real World 
_Our insights could be used in the real world to:_ 

**1) Inform Music Production or Marketing Strategies:** Understanding the key features that define their music could help in creating songs that resonate with their audience. This could guide the production of new songs or the marketing of existing ones.

**2) Understand Audience Preferences and Trends:** By analysing the musical characteristics of popular songs, we can gain insights into what listeners prefer. This could inform decisions related to music production, promotion, and distribution.

**3) Predict the Artist of a Song:** By training a machine learning model on the musical characteristics of songs by different artists, we could potentially predict the artist of a song based on its features or key words. This could be used to develop a feature similar to Shazam's song identification, but for identifying the artist of a song without relying on audio recognition. This could be particularly useful in platforms like radio, streaming services, or any situation where the listener may not have immediate access to the artist information.

**4) Personalised Music Recommendations:** The insights could also be used to improve music recommendation systems. By understanding the musical characteristics that define an artist's songs, recommendation systems could suggest new artists with similar characteristics, potentially improving user satisfaction.

# Our innovative Approaches and Machine Learning Models

**1) Bootstrapping** - We noticed that taylor_data has 530 rows while original_bts_data has 224 rows. In order to match the BTS dataset with the Taylor Swift dataset, we decided to use bootstrapping to randomly sample rows from the dataset and add duplicates or slight variations to increase the overall number of rows of the BTS dataset.
   
**2) Feature Selection** - We performed feature selection using the _Gini Index or Information Gain, using the ExtraTreesClassifier from sklearn.ensemble_. This led us to the top 3 most important features for predicting popularity of each artist, which we also then used to narrow down our data visualisation plots to make exploratory data analysis more clear and understandable, and predict Track Popularity.
   
**3) Trend Analysis** - Plotted the yearly average of each attribute to find how Taylor Swift’s and BTS’s songs have changed over time. This has been used to understand how song attributes have changed over time to potentially match audience preferences.
   
**4) Random Forest Classifier** - To predict the artist of a song based on various features. It trains the model on a training set, makes predictions on a test set, and then calculates and prints the accuracy, precision, and recall of these predictions.
   
**5) SHAP Summary Plot** - _(SHapley Additive exPlanations)_ to analyse and plot the importance of each feature in the Random Forest model.

**6) Ridge Regression** - To predict “Energy” of a song based on various features. It trains this model on a separate training set, makes predictions on a separate test set, and then calculates and prints the explained variance of these predictions.

**7) Adjusted R - squared** - We have used this instead of R - squared as it _adjusts the statistic based on the number of features in the model_. R-squared always increases as you add more features to the model, even if those features are not related to the target variable.

**8) Random Forest Regressor** - To predict Track popularity based on features revealed as important by Feature Selection for each Artist.

# Observations and Inferences 

_Based on the Feature Importance and Exploratory Data Analysis_ - 

**1) The most important features defining Taylor Swift's music are 'speechiness', 'loudness', and 'acousticness'.The most important features defining BTS music are 'speechiness', 'instrumentalness', and 'loudness'.**

**2) Speechiness:-**
Taylor Swift's music tends to have low speechiness, with the majority of her songs having a speechiness of 0.055225 or less. This suggests that her songs contain fewer spoken words.
In contrast, BTS's music has a moderate level of speechiness, suggesting a higher presence of spoken words in their songs compared to Taylor Swift.

**3) Loudness:-**
Both artists have a moderate level of loudness in their music. However, Taylor Swift's music shows a more consistent loudness level, with a peak around -10 dB.
BTS's music, while also moderate in loudness, correlates strongly with energy, suggesting that their louder tracks tend to have more energy

**4) Acousticness:-**
Taylor Swift's music shows a significant portion of low acousticness tracks, but also a minor peak around 0.6, indicating the presence of more acoustic tracks.
BTS's music doesn't highlight acousticness as a defining feature. However, their tracks with more spoken words tend to be more acoustic.

**5) Instrumentallness:-** 
Instrumentalness is not a defining feature for Taylor Swift's music based on the provided analysis. 
For BTS, tracks with higher instrumental content tend to be more danceable.

**6) Correlations:-** 
In Taylor Swift's music, loudness and energy have a strong positive correlation, suggesting her louder songs are more energetic. There's a strong negative correlation between loudness and acousticness, and energy and acousticness, indicating her acoustic tracks are less loud and energetic. 
In BTS's music, speechiness has a strong positive correlation with acousticness and liveness, suggesting their tracks with more spoken words are more likely to be acoustic and live.

_In essence, while both artists share some similarities like the positive correlation between loudness and energy, they exhibit distinct musical characteristics. Taylor Swift's music leans towards a balance of melodic and acoustic elements, while BTS's music tends to favor spoken words, live performances, and danceable, instrumental tracks._

_Based on the Machine Learning Modelling  -_

1) **The RandomForestClassifier was able to perfectly predict the artist of each song in the test set**, with an accuracy, precision, and recall of 1.0. This suggests that the features used are highly indicative of the artist.

2) The Ridge regression model was used to predict the 'energy' of a song. The **R-squared value of 0.81** indicates that about 81% of the variability in 'energy' can be explained by the features used in the model. The **adjusted R-squared value of 0.797** takes into account the number of predictors in the model and is a more accurate measure of the model's performance.

3) **SHAP Analysis:** The SHAP values represent the contribution of each feature to each prediction the model makes. For each song in the training set, the SHAP values provide a detailed breakdown of how much each feature contributes to the model’s prediction of the artist (Taylor Swift or BTS). In the plot, _the red points indicate instances where the interaction of the features increased the likelihood of the song being classified as by Taylor Swift, and the blue points indicate increasing the likelihood of it being a BTS song._

4) The RandomForestRegressor was able to predict popularity based on the important features of each artist well. Given that the **popularity range is from 0 to 100**, the **Mean Absolute Errors (MAEs)** of 5.76 for Taylor Swift and 2.71 for BTS can be considered relatively **low**. Additionally, both models have a relatively **high R^2** of 0.61 and 0.8 for Taylor Swift and BTS respectively.

_Based on the Trend Analysis for Taylor Swift_  -

Taylor Swift's music has seen a gradual evolution over time, with a decrease in energy, popularity, key, liveliness, loudness, danceability, valence, and tempo, suggesting a **_shift towards more introspective and mellow music_**. Despite this, energy and loudness remain significant elements in her music. An increase in danceability, speechiness, acousticness, instrumentalness, and duration indicates a **_shift towards more complex song structures, lyrics, and a greater emphasis on acoustic and instrumental elements._** **A notable spike in acousticness in 2020 aligns with the release of her indie-folk album 'Folklore'.** The analysis highlights Swift's versatility and exploration of different musical styles.

BTS's music, on the other hand, has also evolved, with a decrease in energy, danceability, speechiness, key, acousticness, liveliness, valence, tempo, and duration. This is likely due to their **_shift from hip-hop and rap-centric music to more pop and R&B centric music, as seen in recent releases like "Butter" and "Dynamite"._** Despite this, there's been an **_increase in the popularity_**, loudness, mode, and instrumentalness of their songs, suggesting a **_growing audience_** and a shift towards more musical elements and less speech-oriented content. The trend analysis of BTS reveals a dynamic and evolving musical journey, highlighting the group's experimentation with various musical elements over time.

In essence, both artists have shown significant evolution in their music, with Taylor Swift moving towards more introspective and acoustic music, and BTS shifting from a rap-centric to a more pop-centric style. Both artists have demonstrated versatility and a willingness to experiment with different musical styles and elements.

# Contributors

Ong See Gek Cheryl - Exploratory Data Analysis , Data Visualizations, Trend Analysis

Arun Vasan Keertana - Machine Learning Modeling

Li Yufei - Data cleaning (Bootstrapping), Data extraction, Feature Selection & relations



 



























