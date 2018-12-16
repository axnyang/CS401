# Title
Feminism vs. Sexism in Lyrics: A Portrait of Women in Recent Music

# Data story website
https://axnyang.github.io/CS401/

# Abstract
A 150 words description of the project idea, goals, dataset used. What story you would like to tell and why? What's the motivation behind your project?

Ever since the beginning of the 20th century, a number of political and social movements have arisen with the goal of empowering women and pushing for social equality of sexes. For this ADA project, we are interested in seeing how feminism, and women in general, are represented in the music industry around the world. We would like to explore the topic of feminism since its inception through analyzing the lyrics data set provided by Million Song database, with an emphasis on those lyrics that give us an idea of how women are depicted. Additional lyrics databases might also be used for completion and deeper analysis in natural language processing. We would like to investigate the topic with regards to the different genres of music, the different geographical regions in the world, as well as how it has changed throughout the years. We wonder whether there is a relationship between how women are depicted in lyrics and important political feminism movements, and perhaps the socio-economic status of women across the world may also be reflected in the lyrics.

# Research questions
- How women are being depicted in the lyrics throughout the history of music (throughout time)?
- How the images differ by the genre of music & gender of artist?
- Which words are used in sexist songs versus feminist songs?


# Dataset
We have collected the list of all artists Id ( https://labrosa.ee.columbia.edu/millionsong/sites/default/files/AdditionalFiles/unique_tracks.txt ) which we merged with the genre dataset (msd_tagtraum_cd2c.cls file in http://www.tagtraum.com/msd_genre_datasets.html ). Therefore, the final dataset is the intersection of these two files. Additionnally, we have manually selected and labelled new songs in order to construct a train set for our model. Finally, we have scraped the lyrics of all the english tracks through several web scraping APIs.
 

# Notebooks
For this project, we provide 3 notebooks:
- msd_csv_creation which contains the list of manually selected songs, the scraping function as well as the scraped lyrics dataframes for both the train set and msd dataset and how we export them to csv.
- msd_labelling which loads the train and the msd lyrics dataframes, builds and fits our model and finally, labels the msd dataset ( as feminist, neutral or sexist). We also compute the most correlated unigrams and bigrams in our features ( more details in the notebook).
- msd_vizualisation which loads the labeled msd dataset and creates the relevant plots for the data story.

# Machine learning algorithm
For this project, we have combined the tf-idf model with an linear kernel svm. First, we generate features with the tf-idf transform_fit() function, then we use our feature training data to train a linear svm predictive model, model.fit(X_train, Y_train), and we label our data with model.predict(X_test). The cross-validation procedure gives an accuracy of 64%.

We have also considered several other predictive algorithms. However, linear svm beat them by far.


