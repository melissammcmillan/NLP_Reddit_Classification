# Project 3 - NLP Modelling of Two Reddit Pages by Melissa McMillan

Welcome to My Project 3: Discerning between the r/GameofThrones and r/LordoftheRings pages

**Executive Summary:**

For Project 3, our mission was to utilize two somewhat similar/overlapping subreddits from the Reddit website and run a few Natural Language Processing (NLP) models to try to delineate which posts came from which subreddit page. For further narrative and context, I have a "friend" who is the main subreddit moderator for the r/GameofThrones webpage, and she has a consistent problem in that she often spends time manually removing posts related to the Lord of the Rings on her subreddit page. So, I thought I would try to help her by creating a model that can delineate between Game of the Thrones-related posts and those that should belong on the r/LordoftheRings (r/LOTR) subreddit page instead. Then, my friend could use the model to help filter out the Lord of the Rings posts from the r/GameofThrones webpage. 

To gather data, I use Pushshift's Reddit API to scrape 5,100 post titles and descriptions from each page and put them into a dataframe. I did some cleaning and EDA on each and ultimately decided not to use the post descriptions in my model because there were so many null values between the two datasets. Once I combined my datasets into one large dataframe, I did further EDA and cleaning and explored using a RegEx Tokenizer to filter out some of the text data. Notebook 01 contains the data collection phase of my project and Notebook 02 contains the EDA and Cleaning phase of my project.

After the EDA and cleaning phase, I then began to build some models. I tested both the Multinomial Naive Bayes Classifier and the Random Forest Classifier models to explore which would work best with this dataset. I ran about 20 models between the two types of models, and those can be found in Notebooks 03, 04, and 05. I found that both types of models performed similarly overall, but the best model was a Random Forest Classifier because it had the lowest Recall/Sensitivity score and lowest False Negative score. Those were two key metrics I decided to use for helping my friend because I thought it would be better for her to allow in a small amount of Lord of the Rings posts rather than discard legitimate Game of Thrones posts. 

After running many models and tuning parameters, I found that I was able to create a good model that can help my friend with ~93% accuracy and ~9-10% of the predictions coming up as false negatives. This model was a Random Forest Classifier that utilized a Tfidf Vectorizer and WordNetLemmatizer. This best model can be found in Notebook 05.  

**Problem Statement**

I have a friend who is the main subreddit moderator for the r/GameofThrones webpage, and she has a consistent problem in that she often spends time manually removing posts related to the Lord of the Rings films on her subreddit page. So, I thought I would try to help her by creating a model that can delineate between Game of the Thrones-related posts and those that should belong to the r/LordoftheRings (r/LOTR) subreddit page instead. Then, my friend could use the model to help filter out the Lord of the Rings posts from the r/GameofThrones webpage. The goal of my project is to develop the best classification model that optimizes for accuracy score, Sensitivity/Recall score, and reduces the false negative predictions as much as possible.

---
## Deliverables 

- README file (you are reading it now!): quick summary of project
- Code Folder: These contain my Jupyter Notebooks
    1. 01_Webscraping: This is the starting point for my project. It's where I initially read the data in and condense it into one dataframe and export for Cleaning/EDA.
    2. 02_EDA_and_Cleaning: This is where I initially read the data in and run through the  cleaning and exploration process. 
    3. 03_Naive_Bayes_Modelling_Part1: This has my first ~15 Naive Bayes models to get familiar with testing different parameters and seeing what works best. 
    4. 04_Naive_Bayes_Modelling_Part2: These models use the most clean dataset I made and run final parameters to try to acheive the best NB model I can.
    5. 05_Random_Forest_Modelling: Contains ~5 Random Forest models and has my best overall model for the project.
- Project3_Presentation.zip file: I had to zip my presentation to get it on GitHub. Please open it up to access my presentation files.
- Project3_Presentation in ppt format: this is what I showed to the class
- Project3_Presentation in pdf format: this is the pdf exported version of what I presented to the class
- Data Files: There are 4 files in this folder, here are the details
    1. combined_data_cleaned_with_regexp.csv: this is the final cleaned dataset with emojies, symbols, and special characters removed
    2. combined_data_with_selftext.csv: this is my first-pass cleaned dataset, but still has emojies and symbols in it
    3. got_5100_posts.csv: This is the raw scraped data from the Game of Thrones subreddit page.
    4. lotr_5100_posts.csv: This is the scraped data from the Lord of the Rings subreddit page.
