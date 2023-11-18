# Shifting Scenes: A Deep Dive into Actors' Movie Genre Selections 🕺

## Abstract💭
This study seeks to delve into the intricate choices actors make in selecting roles and the underlying influences guiding these decisions. In a profession that captures the dreams of countless aspiring individuals, an actor's selection of roles not only molds their career trajectory but also leaves a lasting imprint on the audience's cinematic journey. It is noteworthy that many actors embark on diverse movie genres throughout their careers, transitioning, for instance, from a comedic beginning to embracing more serious film genres. Our exploration will systematically examine the scientific criteria for gauging these actor transformations, focusing on analyzing how these shifts impact their careers and elicit responses from the audience. Additionally, we will delve into individual factors influencing actor transformations, such as age, box office revenue, reputation, and societal factors like specific historical periods and evolving social trends.


## Research Question 🔍

Our research focuses on the following five key questions:

1. Which actors tend to stick to a relatively fixed movie genre, and which ones exhibit more versatility? Is there a greater proportion of actors who change genres or those who stay consistent? Are there differences in terms of gender, length of an actor's career, and other factors?

2. In which movie genres are actors more inclined to undergo transitions? Conversely, which movie genres see less variation among actors? From the perspective of an actor's career, is there a discernible pattern in the timing of these transitions?

3. Do actors achieve greater success after undergoing transitions? Is there an improvement in their movie box office performance and ratings? Are there more significant achievements in awards and recognitions?

4. From an individual perspective, why do actors choose to transition? Is it due to a sense of monotony with a particular film style? Or is it because the age factor makes them no longer suited to certain types of movies? Could their decision be inspired by the enormous success of a particular film they were involved in?

5. From a societal perspective, why do actors choose to transition? Are there specific historical periods where the proportion of actors undergoing transitions significantly increased? If yes, is this correlation tied to changes in public viewing preferences, social trends, and societal issues? (Reference to historical context may be required)

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
To compute the number of major changes for each actor, indicating the frequency of genre transitions.
### Time-Series Analysis
To analyze the impact of genre changes by comparing movie ratings, box office revenues, and award nominations across different time periods, involving the collection, aggregation, and comparison of time-series data.
### Network Analysis:
To draw genre transition graphs, using nodes to represent different genres and edges to signify transitions between genres, with the width of the edges representing the number of transitions, helping visualize the pattern of transitions between genres for actors.
### Regression Analysis:
To define a formula that measures the success of a film, such as through a combination of box office earnings, ratings, awards, etc., and to use this formula as the threshold for "treatment" and then conduct an observational study, such as employing a Regression Discontinuity Design to assess whether successful films lead to changes in actors' genres.
### Proportion Tests:
After determining the threshold for successful movies, calculate the proportion of actors who change genres following a successful movie, using proportion tests to compare the rates of genre change between different groups, such as before and after the success.
### Causal Analysis:
Sometimes there are multiple and interrelated measures of a movie's success, causal analysis can be employed to identify underlying dimensions and simplify subsequent regression analyses.

By applying these methods, we will be able to gain insights into the patterns, temporal distributions, and potential influencing factors of actors' genre changes, as well as visualize these dynamics. Furthermore, we will be able to assess the impact of specific events (such as a highly successful movie) on actors' future role choices.

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
