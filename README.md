# Mining-opinion-on-COVID-19-based-on-Twitter-Data

This project is aimed to analyze the sentiment of tweets that contain the word "vaccine" in two different ways and detect any possible misinformation inside them.

First of all, all files mentioned below must be placed in the same folder for the notebooks to properly work. In the GitHub repository they are separated in different folders only for the purposes of clarification and order.

This GitHub repository contains all the Jupyter Notebooks and any additional necessary files for this project to work. More specifically it contains:

1) a folder named "Notebooks" containing the "Libraries", "Connecting", "Collecting", "Sentiment Analysis", "Sentiment Prediction" and "Fake News Detection" notebooks

2) a folder named "Datasets" containing all the datasets used in the "Sentiment Analysis" and "Sentiment Prediction" notebooks as well as the 500000 tweets dataset, all in separate sub-folders

3) a folder named "Images" containing three additional png images used in the "Sentiment Analysis" notebook

Here is a quick summary of the notebooks:

1) Libraries: Here we have all the imported libraries used in all the notebooks. This notebook is executed in every other notebook in order to not import again and again all the necessary libraries in each notebook. The user can change, add or delete any libraries in this notebook and this change will be transferred in all the notebooks.

2) Connecting: In this notebook we connect with the Twitter App and MySQL Workbench. The user does not need to change anything in this notebook as it is executed through "Sentiment Analysis" in order to just connect with the tools. The only tool he needs to download himself is the Workbench only in the case that he wants to access it. If the user does not want to use the Workbench to download new tweets and wishes to use a dataset like mine, he does not need the Workbench at all. If the user wants to connect another Twitter App instead of mine, all he has to do is change the keys at the start of the notebook. This notebook contains questions, that will be asked in "Sentiment Analysis", about how to navigate his Workbench, if of course he chooses to use it, such as if he wants to use existing databases and tables or new ones.

3) Collecting: This notebook is used to stream and collect new tweets by saving some specific features of the tweets such as their text, time and place of creation, the user's id and another feature is always extracted which is the polarity of the text through the use of the TextBlob algorithm. The polarity is always one of the three major sentiments, neutral, positive or negative. All these features create the new tweets dataframe object that will be used the rest of the project. All these downloaded tweets share some common words in their texts that the user chooses on his own, which in our case is the word "vaccine". It is again executed through "Sentiment Analysis" and the user does not have to do anything about it, only in the case that he wants to download new tweets and possibly extract even more features from the tweets. However for this to happen, the user must not only save the features in new variables but also change the code both in "Connecting" and "Collecting" notebooks in the respective SQL queries.

4) Sentiment Analysis: This notebook is the first of the three main processes. It involves the use of the TextBlob algorithm to take the polarity of the tweets and the display of this knowledge in many ways such as with a time series graph and pies for example in order to show the three sentiments. The whole purpose is to see the polarity that TextBlob extracted from these tweets. The user has to answer some questions in the first two cells but after that everything else can be executed without any interruption. A dataset of 500000 tweets, downloaded with this program, is also provided in case the user does not want to download new ones and it can be found in the "Datasets/Tweets" sub folder. Additionally, there are three png files in "Images" folder that are used in this notebook. The two wordclouds are generated throughout the whole process, saved in the current folder where this notebook is and then re-used in the final plot as images. In every execution of the cells that generate the wordclouds, new wordclouds are generated and saved on top of the old ones for any potential changes, which are then used in the final plot as already mentioned. The tweets are again used in the same graphs as before but this time only tweets made in the US are used. In the end we compare everything together to see potential differences between the world against only the US. 

5) Sentiment Prediction: This notebook on the other hand uses a lot of classification algorithms and an LSTM model to predict, rather than extract, the polarity of the tweets. The input data for the classifiers are the datasets inside the "Datasets/Sentiment Prediction Datasets" sub folder. The data is then pre-processed, transformed into numerical arrays, split into training and testing datasets and the training ones are inputted in the models. The models are then trained and each one predicts the polarity of the testing data to get their accuracy scores, while displaying some useful information for each algorithm. The user is free to add or delete any of the classification models or even change their parameters for potentially different results. The user is then asked to choose one of them and finally use it to predict the polarity of our tweets, insert it into the polarity column of a copy of the original dataset, display it again with some graphs, both for the world and US tweets, and finally compare the results with the results of "Sentiment Analysis", in order to see if TextBlob's output is any different from the classification algorithm's output, always regarding the polarity of the tweets.

6) Fake News Detection: Lastly this notebook is exactly the same with "Sentiment Prediction". The only differences are the input datasets, which are found in the "Datasets/Fake News Detection" sub folder, and that the purpose of this notebook is not to predict the polarity of the tweets but to find if they contain any misinformation. After the training of the algorithms and the user's choice for one of the them, the tweets get valued as fake or true and all the fake ones are discarded. Once again we display in graphs, both for the world and US tweets, the polarity of the tweets and compare the results with "Sentiment Prediction's" results, in order to see if the deleted tweets were part of a specific sentiment group or not.

And here is a quick summary of the datasets:

1) Tweets: As explained above it is a collection of 500000 tweets, always containing the word "vaccine", with the four extracted tweet features, all downloaded in August 2021, as well as the polarity the TextBlob algorithm has outputted.

2) Sentiment Prediction Datasets: All datasets in this sub folder are full with tweets of different topics with various columns of which we are only interested in their text as well as in their polarity that humans have valued tweet by tweet. We want to use these tweets as input data for the classification models and we needed texts that have been valued as negative, positive or neutral by real humans and not another algorithm or process. In that way the models train to somewhat understand which words output which emotion and then be able to predict the polarity of our own tweets.

3) Fake News Detection Datasets: All datasets in this sub folder are the same with the datasets in "Sentiment Prediction Datasets" in their basis. They are short articles about news around the world that instead of a polarity attached to them they have a label for being a fake or not story, which is also handled by a human. In the same notion we feed these datasets to the same classification algorithms and get trained models that can predict if our tweets spread misinformation or not.
