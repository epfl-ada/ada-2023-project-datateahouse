# Shifting Scenes: A Deep Dive into Actors' Movie Genre Selections 🕺

## Data Story
Please visit our data story [here](https://xixismile-ops.github.io). The final code is presented in the finalize.ipynb.

## Abstract💭
This study seeks to delve into the intricate choices actors make in selecting roles and the underlying influences guiding these decisions. In a profession that captures the dreams of countless aspiring individuals, an actor's selection of roles not only molds their career trajectory but also leaves a lasting imprint on the audience's cinematic journey. It is noteworthy that many actors embark on diverse movie genres throughout their careers, transitioning, for instance, from a comedic beginning to embracing more serious film genres. Our exploration will systematically examine the scientific criteria for gauging these actor transformations, focusing on analyzing how these shifts impact their careers and elicit responses from the audience. Additionally, we will delve into individual factors influencing actor transformations, such as age, box office revenue, reputation, and societal factors like specific historical periods and evolving social trends.


## Research Question 🔍

Our research focuses on the following five key questions:

1. How do we measure the genre changes of actors during their careers? How can we depict the general patterns in actors' choices of genres and their transformations?
2. Which actors experience fewer genre changes and which experience more?
3. What impact does the era have on the distribution of movie themes? What effect does it have on the actors' choices of movie genres?
4. What is the relationship between personal factors of actors, like height and gender, and their genre changes? How can we make a more specific qualitative and quantitative assessment of these transformations? What deeper social meanings do they imply?
5. Among award-winning actors, are they more inclined to stay in their comfort zones or to try more diverse fields? What drives their subsequent transformations?

## Additional Datasets 📊

### TMDB

We noticed that out of 81,741 films in the original CMU movie dataset, only 8,401 had `box office revenue` data. Since box office performance is a crucial factor in analyzing actor transformation, we aimed to expand this data. Leveraging the [TMDB](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset) dataset, we successfully added 1,797 previously unknown values for `box office revenue`.

### World Bank CPI

We're utilizing [the World Bank CPI dataset](https://data.worldbank.org/indicator/FP.CPI.TOTL.ZG) to adjust `box office revenue` for inflation, setting the U.S. CPI as the benchmark for a consistent financial comparison over time.

### IMDb

To diversify our analysis of a movie's success, we extracted two datasets, `title.ratings` and `title.basics`, from [IMDb](https://datasets.imdbws.com) to add a new dimension to our study of actor transformation.

### Oscar

We included the **Best Actor/Actress** and **Best Supporting Actor/Actress** awards from [The Oscar Award](https://www.kaggle.com/datasets/unanimad/the-oscar-award) dataset to examine the impact of these prestigious recognitions on actor transformation.

### 'Big Three' International Film Festivals

Alongside the Oscars, we also focus on the acting awards of the "Big Three" film festivals—Berlin🐻, Cannes🌴, and Venice🦁. These awards include **Silver Bear for Best Actor/Actress**, **Prix d'interprétation masculine/féminine**, and **Volpi Cup**, we have obtained relevant data from Wikipedia, where can be found in the `ExpandedData` file.

## Methods 🧭

## For milestone2：
### Time Window
Specifically speaking, the key step for us is to detect the changes of genres. According to our observation, most actors changed their genres gradually but not suddenly, making it hard to dicern changes and seperate different period. Therefore, instead of performing analysis directly on the provided movie genres, we choose to use a filter window spanning several movies to increase robustness. To be specific, we employ a sliding window with a span of 3, and meticulously traverse an actor's filmography, chronologically arranged, to pinpoint the genres of the highest frequency within the window, as the example picture shows：
![alt text](https://github.com/epfl-ada/ada-2023-project-datateahouse/blob/main/illustration.jpg)
### Jaccard Similarity
After the first step, we choosed Jaccard Similarity to measure the similarity of two consecutive window values. We use this similarity as the threshold below which a major change is considered occured. We mark those changes and use them to split periods, from which we again extract the most frequently occuring genres as the feature genres that represent that period. To better illustrate, we manually color different periods to observe the number of major changes, different periods, as well as their typical genres.

## For our entire project:
To address our research question, we plan to apply the following data analysis methodologies:
### Descriptive Statistics:
Compute the number of major changes for each actor, group our data by different characteristics of actors, and then describe and compare the distributions of genre changes intra and inter groups.
### Causal Analysis:
Define a formula that measures the success of a film, such as through a combination of box office earnings, ratings, awards, etc., and use its output as the threshold for "treatment". Then we conduct an observational study, such as employing a Regression Discontinuity Design to assess whether successful films lead to changes in actors' genres. We are using matching algorithms to deal with potential confounders to help us draw more reliable conclusions.
### Proportion Tests:
Aftering defining "successful" movies, we get their genres and calculate the proportion of these genres in the periods after that, and compare with the that of the "untreated" groups.
### Time-Series Analysis
We analyze the impact of genre changes by comparing movie ratings, box office revenues, and award nominations across different time periods, involving the collection, aggregation, and comparison of time-series data.
### Data Visualization:
We draw genre transition graphs by using nodes to represent different genres and edges to signify transitions between genres, with the width of the edges representing the number of transitions, helping visualize the pattern of transitions between genres in general.


By applying these methods, we will be able to gain insights into the patterns, temporal distributions, and potential influencing factors of actors' genre changes, as well as visualize these dynamics.

## Proposed Timeline 🗓️

```C
.
├── Week 8  - Data Preprocessing and initial analyis
│  
├── Week 9  - Algorithm optimization and further Analysis
│  
├── Week 10 - Focus on Homework II
│  
├── Week 11 - Final analysis and summary
│  
├── Week 12 - Data story draft
│    
├── Week 13 - Build the website for data story
│  
├── Week 14 - Finalization
.
```

## Team Organization 📝

<table class="tg" style="table-layout: fixed; width: 348px">
<colgroup>
<col style="width: 24px">
<col style="width: 180px">
</colgroup>
<thead>
  <tr>
    <th class="tg-0lax">Teammate</th>
    <th class="tg-0lax">Tasks</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">@Tianhao</td>
    <td class="tg-0lax"> Algorithm design <br> Confounder control and statistical test <br> Causal analysis </td>
  </tr>
  <tr>
    <td class="tg-0lax">@Jingbang</td>
    <td class="tg-0lax"> Data collection and preprocessing <br> Validation of the algorithm <br> Draft of the data story <br> Data visualization and Web development</td>
  </tr>
  <tr>
    <td class="tg-0lax">@Xingyu</td>
    <td class="tg-0lax"> Data collection and preprocessing  <br> Causal analysis <br> Data visualization and Web development </td>
  </tr>
  <tr>
    <td class="tg-0lax">@Xi</td>
    <td class="tg-0lax"> Initial data analysiss <br> Exploratory data analysis  <br> Draft of the data story
  </tr>
</tbody>
</table>
