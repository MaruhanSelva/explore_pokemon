# explore_pokemon: an EDA

### Background
This project is a statistical analysis on 800+ Pokemon using a dataset by Rounak Banik found on Kaggle here: https://www.kaggle.com/rounakbanik/pokemon. This analysis seeks to understand what kinds of pokemon are strong and maybe some reasons why. 

Oftentimes, when playing pokemon games you encounter pokemon that are cute like the electric squirrel Pachirisu or intimidating like Beedrill. What kinds of factors go into choosing the base stats of a pokemon and are there any factors that seem to have a correlation?

Before we start with our exploration, it is important to define what I mean by "strong". While many people calculate this differently, the way that I will be defining strong is by comparing base stat totals as well as individual stats. These stats can make-or-break a battle and it would be kind of cool to see what kind of insights we can gather from this!

Time to be a data detective!

### What we want to know
Let's start by summarizing the questions we have for this analysis!
* How are individual stats AND base stats distributed across all pokemon?
* Is there one best generation of pokemon (based on stats)?
* Are there any attributes of a pokemon that have a correlation with their stats?

### Getting a better feel of the data
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

This data was cleaned to remove most blank values and remove some redundant columns.

### Findings
#### Summary statistics of stat breakdowns
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

<img width="263" alt="Screen Shot 2022-01-13 at 3 31 42 PM" src="https://user-images.githubusercontent.com/75972624/149404821-72a45c86-3b23-4e85-9719-0636f6d49bf7.png">

We can see that generation 4 seems to have some of the strongest original pokemon. It is no wonder that Pokemon Brilliant Diamonds and Shining Pearl were so difficult!

Next, let's see how well each field correlates with each other.

<img width="662" alt="Screen Shot 2022-01-13 at 3 26 04 PM" src="https://user-images.githubusercontent.com/75972624/149404859-d0355414-a8af-4e67-9731-f201efa87c66.png">

Looking at the heatmap, we can see that it seems as though there are not any variables that are strongly postive correlations but we can see that there are some fairly strong negative correlations with base_happiness and capture_rate!

### Conclusion
From this dataset, we were able to answer a couple of our questions. We now know how distributed pokemon's stats are across every single pokemon and across every generation. We were also able to find out which generations had the strongest original pokemon! We were also able to identify some correlations between variables in the dataset.

### Next Steps
Some next steps for this project:
* Have a more in-depth look into the correlation heatmap to see if there is anything else there
* remove some of the outliers to see how the data changes
* Create a generator for some of the best teams in each generation based on this data

#### Thanks for taking the time to go though my project!
