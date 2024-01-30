# explore_pokemon: an analysis and EDA

### Background
This project is a statistical analysis on 800+ Pokemon using a dataset by Rounak Banik found on Kaggle here: https://www.kaggle.com/rounakbanik/pokemon. This analysis seeks to understand what factors make up a legendary pokemon.

Legendary Pokemon are *supposedly* the best of the best when it comes to Pokemon. They should be the strongest, most powerful and most iconic Pokemon within the franchise. Which makes sense or else why would they be legendary in the first place. In this analysis, we want to see what factors can help us predict if a Pokemon has that legendary status.

In this project, we have 3 components: data cleaning, exploratory data analysis (EDA) and modeling.

Time to be a data detective!

### What we want to know
Let's start by summarizing the questions we have for this analysis!
* What are some factors that could influence the legendary status of a Pokemon
* Are there any attributes of a pokemon that have a correlation with their stats?
* Is there a model that we could make in order to be able to accurately predict this?

### Data Cleaning: Getting a better feel of the data
Thankfully, for answering the questions that were established in the section prior, the dataset on Kaggle created by Rounak Banik will help us in our analysis. The link to this dataset is found near at top of the notebook. You can learn a little bit more about the dataset there!

I will start by going over some of the more important columns in the dataset:
* name (of the pokemon) 
* type1 
* type2 (can be null, not all pokemon have 2 types) 
* height_m: the height of a pokemon in metres 
* weight_kg: the weight of a pokemon in kilograms
* capture_rate: the likelihood that a pokemon will be caught in the wild
* baseeggsteps: the amount of steps it takes to hatch a pokemon from an egg
* experience_growth: how fast a pokemon levels up/gains experience
* against_x: how weak a pokemon is to a type
* base_totals: the base stat total
* hp: the pokemon's hp stat
* attack: the pokemon's attack stat
* defense: the pokemon's defense stat
* sp_attack: the pokemon's special attack stat
* sp_defense: the pokemon's special defense stat
* speed: the pokemon's speed stat
* generation: the generation of the pokemon's release
* is_legendary: is the pokemon a legendary?
* percentage_male: the percent that a random pokemon would be male

This data was then cleaned to transform the data in the following ways:
- Removed any Null Values (specifically in the type2 field, height_m, weight_kg and percentage_male fields)
- Removed data inconsistencies and casted to correct data types
- Removed any incorrect data types (Specifically with capture_rate and Minior)

### EDA: Findings
#### Summary statistics of stat breakdowns of all Pokemon
<img width="694" alt="Screen Shot 2022-01-13 at 3 23 05 PM" src="https://user-images.githubusercontent.com/75972624/149404016-ff5b9d1d-3c49-4776-ac0e-ff6163eb5a8b.png">
<img width="607" alt="Screen Shot 2022-01-13 at 3 23 36 PM" src="https://user-images.githubusercontent.com/75972624/149404020-3738bf71-3367-44c2-a407-256eb013d373.png">
<img width="590" alt="Screen Shot 2022-01-13 at 3 23 51 PM" src="https://user-images.githubusercontent.com/75972624/149404136-d84a0fb4-6e7d-4ddd-ab64-672ff7df7e01.png">

Next, let's look at the boxplots to get a better idea of how the data is distributed and to see if there are any outliers.
<img width="629" alt="Screen Shot 2022-01-13 at 3 24 10 PM" src="https://user-images.githubusercontent.com/75972624/149404142-f57c35dd-82cb-4b1b-be86-1f4df2294326.png">
<img width="701" alt="Screen Shot 2022-01-13 at 3 24 24 PM" src="https://user-images.githubusercontent.com/75972624/149404163-1fa312c7-fb44-4a74-a11a-b19016d66351.png">
<img width="587" alt="Screen Shot 2022-01-13 at 3 24 39 PM" src="https://user-images.githubusercontent.com/75972624/149404444-1b9a055f-fc21-49cb-af99-c04281949eca.png">

As we can see, every stat has outliers but oddly enough, the base stat totals do not have any outliers. Thankfully, this is pretty explainable. All base stat totals are below 680 which is exclusively reserved for some pokemon with legendary status (and there are a couple of these).

We can also see that most pokemon's attack stat tends to be their highest stat.

Now let's see each generation stands up to see if a particular generation has harder to beat pokemon!

<img width="642" alt="Screen Shot 2022-01-13 at 3 25 05 PM" src="https://user-images.githubusercontent.com/75972624/149404536-5016dba4-528f-4980-81c5-0a8700acc1d3.png">
<img width="678" alt="Screen Shot 2022-01-13 at 3 25 30 PM" src="https://user-images.githubusercontent.com/75972624/149404543-f4562955-9042-4717-b0ac-823b72e5599e.png">
<img width="665" alt="Screen Shot 2022-01-13 at 3 25 48 PM" src="https://user-images.githubusercontent.com/75972624/149404597-faa73e2b-c4c4-4a44-89c6-c430688b833a.png">

These histograms might not be the best way to find out the best generation simply because there are a different number of pokemon released in each generation! To get a little bit more of a clearer picture, let's use the median of each generation as the mean might be a little bit more skewed due to the prevalence of outliers!

<br>

<img width="263" alt="Screen Shot 2022-01-13 at 3 31 42 PM" src="https://user-images.githubusercontent.com/75972624/149404821-72a45c86-3b23-4e85-9719-0636f6d49bf7.png">

We can see that generation 4 seems to have some of the strongest original pokemon. It is no wonder that Pokemon Brilliant Diamonds and Shining Pearl were so difficult!

Next, let's see how well each field correlates with each other.

<img width="737" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/1fba06a0-6e20-44b0-af7d-682cb85c706b">

Looking at the heatmap, we can see that it seems as though there are not any variables that are strongly postive correlations but we can see that there are some fairly strong negative correlations with base_happiness and capture_rate!

#### Legendary Pokemon Exploration

Now, its time to look more specifically at the Legendary Pokemon in the dataset. In total, we have a total of 70 legendaries across 7 generations. Let's see how they are distributed by generation:

<img width="383" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/a177164f-cd0d-4c32-82b1-59c5f6f8285b">

As we can see, we have an upward trend, i.e. as generations go up, the number of legendaries go up too. Which could be an important feature for out model.

We also have the following trends for height and weight:

<img width="386" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/f748c759-4a13-4e41-bc8b-de3003221314">

<img width="383" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/d4a41eab-2083-4b2f-8865-88c7c5e839a5">

We can see that for the most part, all legendaries don't really have much of a difference compared to regular pokemon with respect to these metrics.

Next, we'll look at base stat totals and legendaries.

<img width="385" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/aa4a63c1-ed0e-4edd-97c6-d12ed0c68c4d">

We can see that most legendaries have a higher base stat total, so it would be a good feature to include in the model.

Lastly, let's look at type (type 1 and type 2) breakdowns for legendaries.

<img width="710" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/4096eb8f-947e-4d30-a324-ad0c257b8676">

<img width="712" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/ee1a970d-12b8-490d-bffa-4b6f4f446f96">

and the sum of these two: 

<img width="724" alt="image" src="https://github.com/MaruhanSelva/explore_pokemon/assets/75972624/457d0a37-1e54-4fea-8838-49cec03c70a9">

We can clearly see that most legendaries have the primary type as psychic and that a lot of legendaries have a secondary type as flying. Looking at the sum of these two (the third plot), we can see that there are very little poison, ground, normal, ghost, dark, ice and bug legendary pokemon. The types will be an important feature for our models.

### Modeling

In this step, I wanted to make a model that would be able to correctly classify a Pokemon as a legendary (or as a non-legendary). To do this, I used scikit-learn and used the Decision Tree and RandomForests Models. When I had fit the full models using all the data (that wasn't unique), i got the following mean squared errors:

* Full Decision Tree: 0.014925373134328358
* Full Random Forests: 0.014776119402985073

We see that Random Forests is slightly better than Decision Trees. I also looked at doing a reduced model using the features that we found interesting in the EDA (types, base_total and generation)

We found the following MSEs:

* Reduced Decision Tree: 0.05223880597014925
* Reduced Random Forests: 0.04820066334991708

These two are not better than the full model. So it seems that we'll have to look at some other factors to see how we can go about creating a better model (feature engineering).


### Conclusion
From this dataset, we were able to answer a couple of our questions. We now know how distributed pokemon's stats are across every single pokemon and across every generation. We were also able to find out which generations had the strongest original pokemon! We were also able to identify some correlations between variables in the dataset. We also were able to create some basic classification models.

### Next Steps
In the future, some next steps I have for this project:
* Feature Engineering
* Cross-Validation
* XGBoost
* Compare the model to data from future generations

#### Thank you for taking the time to go though my project!
