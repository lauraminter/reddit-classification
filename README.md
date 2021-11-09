# Reddit Classification Project
by Laura Minter
November 2021

## Problem Statement
Our goal is to identify common and disparate themes in the reddit posts to for Portland and Seattle subreddits that could be useful for marketing campaigns across the Pacific Northwest.  

## Background
Reddit is an active online community that provides targeted marketing opportunities.  We are interested in looking specifically at subreddits related to large markets in the Pacific Northwest (PNW).  We are interested in identifying themes that would work across the PNW as well as in the individual city markets.  

## Data
We use the `r/Seattle`, `r/SeattleWA`, and `r/Portland` subreddits accessed via the Pushshift API.  We look at 120k Seattle-based posts (half from each subreddit) and 150k from Portland-based posts.  Our overall data set was approximately 270k posts from approximately 85k unique authors.  

We used the title, text and author information as retrieved from Pushshift.  We vectorized the combined title and text using the TFIDF vectorizer and the CountVectorizer.  

## Model
To demonstrate our understanding of the data we built a logistic regression model to distinguish between posts sourced from Seattle and from Portland.  Our base model showed 82.5% accuracy on unseen data with low variance and a quick fit.  We tried multiple other models (decision tree, bagged trees, SVC, xgboost) which took longer and showed no increase in performance.  We selected the logistic regression model given the performance and interpretability as well as speed.  

## Results
The coefficients of the logistic regression revealed that place names are the highest distinguishing factor between the two subreddits.  Many of these are neighborhood names or names or street names.  

Looking at coefficients that are closer to 0 indicates many more local place names but we start to see more non-place words.  The coefficients alone are not enough to tell us if the word is a theme so we restrict ourselves to top used words.  

When we look at both the coefficients and the top 100 in each city we see a few themes emerge.  

We see lots of differences when we look at words that appear on the top 100 in only one of the cities.  By narrowing our focus to top words that also help us distinguish we can further identify disparate themes.  

Seattle is much more likely to use advice-related words like 'suggestion' and 'recommendations.'  

Portland is much more likely to us purchase-related words like 'buy' and 'money.'  


Seattle also has more references to weather-related words like 'rain', 'cloudy' and 'wind' as well as high occurences of 'chance' and 'mph' which are not conclusively weather related but often used in that context.  


Portland is much more likely to reference friends while Seattle is more likely to reference kids, parents, and adults.  Experience tell us that these references may not be positive and sentiment analysis on these may provide more insight.  


Unsurprisingly both locations are more likely to use their own location words like city and state names as well as other hyper local place names like neighborhoods and street names.  

Both locations also use the words 'free' and 'food' at high rates as well as 'downtown' and 'community.'  

## Suggestions and Recommendations
Reddit has an active PNW community, providing a good advertising opportunity.  Across the two markets we see roughly 86k unique authors publishing in the last two years.  

Marketing campaigns across the PNW can focus on community and local events as well as references to local places (e.g., neighborhoods, streets)

For Seattle, references to weather and family (kids, parents) are common and could provide good themes for marketing campaigns.  

For Portland, bikes and friends are references at high frequency and could be good themes for marketing.    


For the next step we could look at time variation in themes.  Investigating the historical seasonality and time variation of top words could help determine if we could build a tool to capitalize on real-time information about reddit posts.  
