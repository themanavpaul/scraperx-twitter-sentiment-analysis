# ScraperX : Twitter Scraper with Sentiment Analysis

- [Part 1:](#part1) Python script fetches tweets from a specified Twitter user, extracts relevant data, and saves it to a CSV file.
- [Part 2:](#part2) Dataset (CSV File) will follow Data Pre-Processing Techniques (Data Cleaning).
- [Part 3:](#part3) Sentiment Analysis Will be Applicable on the Cleaned Dataset.

<br>

## 👋🏻 Hey Software Engineers! 

I'm [Manav Paul](https://linktr.ee/themanavpaul), a 24-year-old spiritual developer on a mission to demystify Generative AI and Machine Learning. Fascinated by its potential, I'm embarking on a 30-day journey to master this cutting-edge technology. This repository is my digital travelogue, where I'll share insights, experiments, and code as I unravel the secrets of AI and ML.

👨🏻‍💻 Connect with me on [LinkedIn](https://www.linkedin.com/in/manav-paul/) and [X(Twitter)](https://x.com/themanavpaul).

<br>

## 🚀 **Features:**

* Fetches tweets from a given Twitter user.
* Handles Twitter API rate limits with retries and exponential backoff.
* Monitors internet connectivity and resumes scraping upon reconnection.
* Saves tweet data to a CSV file with relevant fields.
* Includes a threshold date to stop scraping older tweets.
* Handles potential errors and exceptions gracefully.

## 🎯 **Possible Use Cases (Illustrative):**

* **Data Analysis:** 
    * Analyze tweet sentiment over time.
    * Study the frequency of keywords or hashtags used by a specific user.
    * Identify trends in the user's tweeting behavior.
* **Research:** 
    * Collect data for research projects related to social media, linguistics, or political science.
* **Learning:** 
    * Understand web scraping techniques and Python programming concepts.
    * Explore data handling and manipulation with Python libraries (e.g., `pandas`).

## **Dependencies:**

* `asyncio`
* `csv`
* `datetime`
* `dotenv`
* `requests`
* `twikit`

<br>

# 👩🏻‍💻 Part 1 : ScraperX with Virtual Environment Setup <a name="part1"></a>

The Only Python Script File you need : [ScrapeX](https://github.com/themanavpaul/scraper/blob/main/main.py)

This guide outlines the steps to set up a virtual environment, install dependencies, and run the Python script for fetching tweets from a specified Twitter user.

**Prerequisites:**

* Any operating system (We used Ubuntu)
* Basic understanding of terminal commands

## **Steps:**

1. **Update package lists:**

   ```bash
   sudo apt update
   ```
   This command refreshes the list of available packages from the Ubuntu repositories.

2. **Upgrade existing packages:**

   ```Bash
   sudo apt upgrade
   ```
   This command upgrades any outdated packages on your system to ensure you have the latest versions.

3. Install `python3-pip` (if not already installed):

   ```Bash
      sudo apt install python3-pip
   ```
   
   This command installs the pip package manager for Python 3, which is necessary for installing Python libraries.

4. Install python3-venv (if not already installed):

   ```Bash
      sudo apt-get install python3-venv
   ```
   
      This command installs the venv module, which is used to create virtual environments for Python projects.

5. **Create a virtual environment:**

   ```Bash
      python3 -m venv my_env_project
   ```
   
   Replace my_env_project with your desired virtual environment name. This command creates a virtual environment directory named my_env_project in your current working directory.

6. **Activate the virtual environment:**

   ```Bash
      source my_env_project/bin/activate
      # For Linux/MacOs Users
   ```
   ```Bash
      myenv\Scripts\activate
      # For Windows Users
   ```
   
   This command activates the virtual environment. You'll see the name of the virtual environment prepended to your terminal prompt, indicating that you're now working within the isolated environment.

7. **Verify environment activation (optional):**

   ```Bash
      python
   ```
   
   This command (without arguments) will typically display the Python version within the virtual environment. If you see the correct Python 3 version, you've successfully activated the environment.

<br>

## **Installation and Execution:**

1. Install required packages using pip:

   ```bash
   pip install python-dotenv requests twikit
  
2. Usage:

  - Save the script: Save the provided code as `main.py`.

  - Run the script:

    ```Bash
    python main.py
    ```

3. Input your Twitter API credentials and make sure you're logged-in in as well:
  
   ```bash
     Enter your Username=<your_twitter_username>
     Enter Your E-MAIL=<your_email>
     Enter you Password=<your_password>
   ```
     Note: This part will handle the authetication.

   Input the twitter account username you wish to scrape (eg. elonmusk, realdonaldtrump)

   ```bash
      Enter the twitter account username you wish to scrape: <desired_twitter_account>
   ```
    
---

<br>

## **Script Functionality:**

- **Fetches tweets:** Retrieves tweets from the specified Twitter user in batches.
- **Handles rate limits:** Implements mechanisms to handle Twitter API rate limits, including exponential backoff and retries.
- **Checks internet connection:** Monitors the internet connection and waits for reconnection if it's lost.
- **Stores data in CSV:** Saves fetched tweets to a CSV file with relevant information (tweet ID, content, created at, etc.).
- **Threshold date:** Allows you to specify a threshold date. The script will stop fetching tweets if it encounters tweets older than the threshold.
- **Error handling:** Includes basic error handling for various exceptions.
  
<br>

> **Disclaimer:**
This script is provided for **educational and experimental purposes only**.
Use this script responsibly as it does **not** utilize the official Twitter API and may become **deprecated** in the future due to potential changes in Twitter's website structure or data availability. 
The author is not responsible for any misuse or consequences of using this script.
Use this script with caution and at your own risk.

---

<br>

# 📗 Part 2 & 3 : Data Pre-Processing + Dataset Sentiment Analysis

Your Dataset Created : [Twitter_Dataset.csv](https://github.com/themanavpaul/scraperx-twitter-sentiment-analysis/blob/main/ceo_tweets_2024.csv)

Here is the Jupyter Notebook with all the commands and techniques : [ScrapeX_Sentiment_Analysis.ipynb](https://github.com/themanavpaul/scraperx-twitter-sentiment-analysis/blob/main/ceo_tweet_analysis.ipynb)

Model used for Sentiment Analysis : [Roberta](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment)

## 🔰 Step 1 :  **Data Pre-Processing** <a name="part2"></a>

**1. Introduction**

* **Project Overview:** Briefly describe the purpose of cleaning the scraped Twitter data and the intended use of the cleaned dataset (e.g., sentiment analysis, topic modeling).
* **Data Source:** Specify how the Twitter data was obtained (e.g., Twitter API, web scraping).
* **Data Description:** Provide a high-level overview of the raw data, including:
    - Number of tweets.
    - Data fields present (e.g., tweet content, source, timestamp).
    - Data format (e.g., CSV, JSON).
    - Any initial observations about the data quality (e.g., missing values, duplicates, inconsistencies).

**2. Data Loading and Exploration**

* **Loading the Data:** Describe the steps involved in loading the Twitter data into your Jupyter Notebook environment. Mention the libraries used (e.g., pandas).
* **Initial Exploration:** Summarize key characteristics of the dataset using techniques like:
    - `df.head()` and `df.tail()` to view the first and last few rows.
    - `df.info()` to get data type information and check for missing values.
    - `df.describe()` to get summary statistics for numerical columns (if applicable).
    - Visualizations (histograms, scatter plots) to understand data distributions and relationships (if relevant).

**3. Data Cleaning Steps**

* **Handling Missing Values:**
    - Identify columns with missing values.
    - Explain the chosen strategy for handling missing data (e.g., deletion, imputation, leaving as is).
    - Justify your approach based on the data and analysis goals.
* **Removing Duplicates:**
    - Describe the criteria used to identify duplicate tweets (e.g., exact content matches, duplicates based on specific fields).
    - Explain the method used to remove duplicates (e.g., `df.drop_duplicates()`).
* **Data Transformation and Feature Engineering (if applicable):**
    - Describe any transformations applied to the data, including:
        - Data type conversions (e.g., converting strings to dates).
        - Feature engineering (creating new features based on existing ones).
    - Provide justification for each transformation.
* **Text Preprocessing (if applicable):**
    - If dealing with textual data (tweet content), describe the text cleaning techniques used:
        - Removing punctuation, stop words, URLs, mentions.
        - Tokenization (splitting text into words).
        - Stemming/lemmatization (reducing words to their base form).
    - Explain the rationale behind each preprocessing step.

**4. Data Validation and Quality Checks**

* **Data Consistency Checks:**
    - Describe how you ensured data integrity (e.g., verifying data ranges, checking for inconsistencies between related columns).
* **Data Quality Assessment (optional):**
    - Discuss any metrics used to evaluate the quality of the cleaned data (e.g., data completeness, accuracy, consistency).

**5. Saving the Cleaned Data**

* Describe how you saved the cleaned dataset (e.g., CSV, pickle file).
* Specify the file path and name.

Sure, here is the documentation for sentiment analysis for twitter in a structured format:

<br>

## 🔰 Step 2 :  **Sentiment Analysis of Twitter Data** <a name="part3"></a>

Model used for Sentiment Analysis : [Roberta](https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment)

This document outlines the steps involved in performing sentiment analysis on a dataset of Twitter conversations. The code utilizes libraries like pandas, transformers, matplotlib, and seaborn.

**1. Model Building:**

This section outlines the process of loading a pre-trained sentiment analysis model and defining a function to predict sentiment for individual tweets.

* **Tasks:**
    * Imports libraries like `torch` and `transformers`.
    * Loads a pre-trained sentiment analysis model ("cardiffnlp/twitter-roberta-base-sentiment") along with its tokenizer.
    * Defines a function `predict_sentiment` that:
        * Tokenizes the input text from a tweet.
        * Moves the tokens to the same device (CPU or GPU) as the model.
        * Uses the model to predict sentiment probabilities (Negative, Neutral, Positive).
        * Identifies the sentiment with the highest probability and returns it as the sentiment label.
* **Output:**
    * A DataFrame with a new column named "Sentiment" containing the predicted sentiment for each tweet.

**2. Sentiment by Username:**

This section focuses on visualizing sentiment distribution across different usernames.

* **Tasks:**
    * Groups the DataFrame by username and sentiment to count the occurrences of each sentiment for each user.
    * Creates a grouped bar chart using seaborn to visualize the sentiment distribution for each username.
* **Output:**
    * A bar chart depicting the sentiment distribution (Negative, Neutral, Positive) for each user.

**3. Sentiment Retweets and Likes by Username:**

This section explores the engagement metrics (retweets and likes) grouped by sentiment and username.

* **Tasks:**
    * Iterates through engagement metrics (retweets and likes).
    * For each metric, creates a bar chart using seaborn to visualize the distribution of the metric (retweets/likes) across sentiments for each user.
* **Output:**
    * Two separate bar charts, one for retweets and another for likes, depicting the distribution of these metrics for each sentiment and username.

**4. Sentiment Distribution Count:**

This section generates a simple count plot to understand the overall sentiment distribution in the data.

* **Tasks:**
    * Creates a count plot using seaborn to visualize the total number of tweets categorized as Negative, Neutral, and Positive.
* **Output:**
    * A bar chart showing the sentiment distribution (count) of Negative, Neutral, and Positive tweets.

**5. Sentiment Metrics (Retweets, Likes):**

This section explores the relationship between sentiment and engagement metrics (retweets and likes).

* **Tasks:**
    * Iterates through engagement metrics (retweets and likes).
    * For each metric, creates a bar chart using seaborn to visualize the average retweet/like count for tweets categorized as Negative, Neutral, and Positive.
* **Output:**
    * Two separate bar charts, one for retweets and another for likes, depicting the average retweet/like count for each sentiment category.

**6. Sentiment Distribution by Username (Stacked Bar Chart):**

This section presents a stacked bar chart to visualize the sentiment distribution for each user.

* **Tasks:**
    * Prepares the data for a stacked bar chart by grouping tweets by username and sentiment and calculating the count for each sentiment category.
    * Creates a stacked bar chart using pandas to visualize the sentiment distribution (Negative, Neutral, Positive) for each user.
    * Annotates the bars with the respective sentiment counts for better readability.
* **Output:**
    * A stacked bar chart where each bar represents a user, and the segments within the bar represent the counts of Negative, Neutral, and Positive tweets for that user.

**7. Wordcloud:**

This section (optional) generates a wordcloud to visualize the most frequent words used in the tweets.

* **Tasks:**
    * Defines a function `generate_wordcloud` that:
        * Takes a DataFrame and the column name containing the tweet text as input.
        * Concatenates all the tweet text into a single string.
        * Generates a wordcloud using the `wordcloud` library to visualize the most frequent words.
    * Applies the `generate_wordcloud` function to the "Cleaned Content" column (assuming it contains the cleaned tweet text).
* **Output:**
    * A wordcloud image depicting the most frequent words used in the tweets, with larger words representing higher frequency.

**8. Saving Files and Model:**

This section (optional) demonstrates how to save the processed DataFrame and the sentiment analysis model for future
* Save & Download the Updated CSV file.
* Save and Download the Model using pickle.

---

<br>

## License

This project is licensed under the [**MIT License**](https://opensource.org/licenses/MIT).

**Copyright (c) Manav Paul 2024**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, distribute, sublicense, and/or sell copies of the Software,
and to permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
THE SOFTWARE.

