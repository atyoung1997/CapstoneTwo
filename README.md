# CapstoneTwo
Springboard Unit 7 Capstone Two

# Purpose
The purpose of this project was to take a random dataset, clean it, extract useful features, and apply several different modeling techniques to try to predict sales numbers for each video game.

# Challenges
After starting this project I quickly noticed that the data would not be conducive to a highly predictive model. This was for a few main reasons:
1. By default there are only 4 predictor variables available for each video game: year, genre, publisher, and platform
2. Aside from Year, each of the 3 other predictor variables are categorical variables with many different levels (500+ in the case of publisher)
3. If you know anything about videogames, you will also know that within each of these three categorical variables there is a large amount of variance in sales (none of them are great predictors). For example, each genre has both very high and very low selling games, and the same holds true for the platform and publisher variables
4. The dataset only included data for titles with over $100K in global sales, which likely obscured some of the broader trends that would separate ultra low selling games form ultra high selling games.

While this dataset was not great for producing a highly predictive model, it did allow me to explore different methods of dealing with this type of data. The following are some steps that I took to try to create the best possible model given the low quality data:
1. Re-leveled the categorical data to reduce granularity
2. Created more useful categories from the already existing categories: i.e. created a Platform Type variable (levels = [console, mobile, PC]) from the existing platform variable
3. Created a new numeric feature which was the average sales per title for a given Publisher for titles released before the title that was being evaluated. When evaluating feature importances in the Random Forest model that I ran, this ended up being the most important feature by far. 
4. Turned the regression problem into a classification problem (i.e. predict whether a video game would have over $500K in sales)
5. Performed a cross-validated grid search to optimize hyper parameters of the final random forest classifier, including max depth, min samples per leaf, and class imbalance strategies. 