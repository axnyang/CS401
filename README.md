# Title
Feminism and How Women are Depicted Through Lyrics

# Abstract
A 150 words description of the project idea, goals, dataset used. What story you would like to tell and why? What's the motivation behind your project?

Ever since the beginning of the 20th century, a number of political and social movements have arisen with the goal of empowering women and pushing for social equality of sexes. For this ADA project, we are interested in seeing how feminism, and women in general, are represented in the music industry around the world. We would like to explore the topic of feminism since its inception through analyzing the lyrics data set provided by Million Song database, with an emphasis on those lyrics that give us an idea of how women are depicted. Additional lyrics databases might also be used for completion and deeper analysis in natural language processing. We would like to investigate the topic with regards to the different genres of music, the different geographical regions in the world, as well as how it has changed throughout the years. We wonder whether there is a relationship between how women are depicted in lyrics and important political feminism movements, and perhaps the socio-economic status of women across the world may also be reflected in the lyrics.

# Research questions
- How women are being depicted in the lyrics throughout the history of music (throughout time). 
- How the images differ by the regions in the world (U.S. vs European).
- How the images differ by the genre of music & gender of artist.

These are some guidelines of what we would like to explore. Before we start exploring, we also need to answer questions such as:  
- How do we measure the "image" of women, or how to make the "image" of women quantifiable? 
- Would we like to make it a binary classification problem, simply a positive vs. negative image, or more multi-class problem?
- Which NLP tools should we use for the classification?
- How do we optimize visualization to deliver our messages in the most powerful way? 


# Dataset
List the dataset(s) you want to use, and some ideas on how do you expect to get, manage, process and enrich it/them. Show us you've read the docs and some examples, and you've a clear idea on what to expect. Discuss data size and format if relevant.

- Million Song Dataset Since the data set contains non-English music, the first step would be to extract music that contains English to create a subset of the data to work with.
- We would also like to use Genius for some additional lyrics (https://genius.com/), and also to enrich the Million Song Dataset which only works with BOW model (Scraping data from genius allows us to use n-gram model for further NLP processing)
- If necessary, we can also do some web scraping for other genre specific music

We can use user-based playlists/databases in order to base our analysis on reference songs and the lyrics they contain
Playlists that contain user-classified feminism songs:

https://8tracks.com/explore/feminist
https://8tracks.com/explore/feminism
https://open.spotify.com/playlist/2WCq1DxfbhTu4tTLslwg1j
https://itunes.apple.com/us/playlist/essential-feminism/pl.d77e6f4bed1b4bbe8140fe87cf00836f?fbclid=IwAR1FqLBiGn4gIjeXL9hPjD6SEcAoz72sfpPhxJhBrIawJIcBokOR_FtP0XI
https://open.spotify.com/playlist/0BaU0irP86ZvXKxbpgXQxe
https://www.azlyrics.com 
 

# A list of internal milestones up until project milestone 2
Add here a sketch of your planning for the next project milestone.

Nov 4th, 2018 - Nov 11th, 2018
- Set up git repo and project skeleton (due Nov 4th)
- Figure out what is in the cluster and find a way to extract the lyrics dataset
- Add the genius dataset, Web Scrape additional lyrics and merge everything in a single dataset 

Nov 11th, 2018 - Nov 19th, 2018
- Filter data with genre, year, and language
- Explore relationship between lyrics relevant to feminism and their genre, year, and production region 

Nov 19th, 2018 - Nov 25th, 2018
- Visualize Data through a variety of format (graphs, maps etc.)
- Discuss narrative of data story 
- Set up goal for next milestone


# Questions for TAs
Add here some questions you have for us, in general or project-specific.

1. About the feminism related playlists: how can we use that information to improve our analysis of the image of women in the bigger datasets (Million songs etc..)?
 
2. Should we design ourselves a model for defining positive and negative image of women in the lyrics? Or perhaps we take an existing model (if there is one)?  
 
3. Do we have enough content to complete a meaningful project? 

4. Can we use some external datasets with the provided one?

# Milestone 2

For the data collection, we have based ourselves on the Million Song Dataset. From this huge data, we are only interested in four attributes:
- The track id
- The artist name
- The year
- The title

In addition to that, we are also interested in the genre of the songs. Luckily, in the Million Song Dataset website, there is already a dataset with the track id and the genre. Thus, we downloaded the corresponding file. We have the genre information for around 191'000 songs. Moreover, we have direct access to the 4 attributes through an additional dataset of around 500'000 songs provided in the Million song website. 

We decide to limit our analysis on this dataset for two reasons. First, manipulating the whole million songs dataset is both time consuming and would require the use of the cluster. Second, after a fast and simple instruction, we discovered that around 150'000 of the genre id are already in the subset we have found.

Next, we use the API we mentionned during Milestone 1 to scrap and collect the lyrics. However, we couldn't find the lyrics of half our dataset. We have decided to keep looking for other alternatives to find the lyrics as they are of paramount importance in our project. Alternatively, we can use an additional dataset from the million song website containing bag of words data. We would like to avoid this alternative as it is a simple count of words in the songs and it removes them from the context in the songs.

In our notebook, we have performed a first descriptive analysis of the merged datasets. The big proportion ( 41%) of the songs' genre is rock. Moreover, although the values of the year attribute range from 1920 to 2010, 91% of the tracks are from the 1980 to 2010. We believe this is due to the rapid growth of Rock from its birth in the fifties to achieve more than 50% of the music industry in the 70s to 80s. In our notebook, we have a plot showing this evolution. In our analysis, due to the genre unbalance, we will use a random subset of the rock music ( or the decade) to balance out the classes.
