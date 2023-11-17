# Breaking the Mold: A Deep Dive into Actors' Role Choices 🕺

## Abstract💭
This study seeks to delve into the intricate choices actors make in selecting roles and the underlying influences guiding these decisions. In a profession that captures the dreams of countless aspiring individuals, an actor's selection of roles not only molds their career trajectory but also leaves a lasting imprint on the audience's cinematic journey. It is noteworthy that many actors embark on diverse roles throughout their careers, transitioning, for instance, from a comedic beginning to embracing more serious film genres. Our exploration will systematically examine the scientific criteria for gauging these actor transformations, focusing on analyzing how these shifts impact their careers and elicit responses from the audience. Additionally, we will delve into individual factors influencing actor transformations, such as age, box office revenue, reputation, and societal factors like specific historical periods and evolving social trends.


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

The key step is to **detect the changes of genres**. While seeming a simple question, it could be especially troublesome when you design an algorithm without having idea of which time period to compare with. It will lose a lot information if we only compare each movie with his/her first movie, and it doesn't make sense either to compare two consecutive movies since it is easily influenced by temporary changes, e.g. try a new genre only once just for fun. In fact, according to our observation, most actors changed their genres gradually but not suddenly, making it even harder to dicern changes and seperate different period. Therefore, we propose to use a filter window spanning several movies, which sildes through the whole career of each actor, and at each time step extracts the most frequent genres within it. As the example picture shows, this algorithm is robust to tempory changes and generates relative stable output compared with the original movie genres. Furthermore, we use Jaccard Similarity to measure the similarity of two consecutive window values. We set the max similarity as threshold, under which we assume there is a big change occurs between two periods. We can then use these labels to split different periods, from which we again extract the most frequently occuring genres as the "feature genre" representing that period. To better illustrate, we manually color different periods, and specially, we refer to those periods of length one as "transition periods", and color them grey.

By doing this, we yield the number of major changes, different periods, as well as their typical genres, for each actor. Along with existing and additional attributes (movie ratings, award nomination, etc.) we can formulate our research questions as descriptive statistics tasks and observational studies cases. Specifically, we plan to:

1. address the question of "Who change their genres" by counting the number of major changes for each actor;

2. analyze the effects of genre change by aggregating and compare the movie rating, movie revenue, number of award nomination etc. of two consecutive periods, or multiple kinds of combination of periods;

3. visualize the genre transition by plotting a transition plot, where two identical columns record different genres and we use arrows and magnitudes to denote the transition and its number between genres two columns;

4. study the pattern of timing of changing genres by analyzing the quantiles of "major change" labels in each actor's career;

5. answer "whether a hugely successful movie would impact actor's changing decision" by defining an equation which measures the success of movies and thresholding them as the "treatment" of observation studies. And then we calculate the proportion of the genres of these movies that appear afterwards as outcomes.

6. study the influence of movie genre itself on changing by comparing the lengths of periods featured by different genres.



The key step is to detect changes in genres. While this may seem like a simple question, it could be especially troublesome when designing an algorithm without an idea of which time period to compare with. It would lose a lot of information if we only compared each movie with actor's first movie, and comparing two consecutive movies is easily influenced by temporary changes, for example, trying a new genre only once just for fun. In fact, according to our observations, most actors change their genres gradually rather than suddenly, making it even harder to discern changes and separate different periods. Therefore, we propose using a filter window spanning several movies, which slides through the entire career of each actor. At each time step, it extracts the most frequent genres within it. As the example picture shows, this algorithm is robust to temporary changes and generates relatively stable output compared to the original movie genres. Furthermore, we use Jaccard Similarity to measure the similarity of two consecutive window values. We set the maximum similarity as a threshold, under which we assume a big change occurs between two periods. We can then use these labels to split different periods, from which we again extract the most frequently occurring genres as the "feature genre" representing that period. To better illustrate, we manually color different periods, and specifically, we refer to those periods of length one as "transition periods," coloring them grey.

By doing this, we yield the number of major changes, different periods, as well as their typical genres for each actor. Along with existing and additional attributes (movie ratings, award nominations, etc.), we can formulate our research questions as descriptive statistics tasks and observational study cases. Specifically, we plan to:

Address the question of "Who changes their genres" by counting the number of major changes for each actor.

Analyze the effects of genre change by aggregating and comparing movie ratings, movie revenue, the number of award nominations, etc., of two consecutive periods, or multiple kinds of combinations of periods.

Visualize the genre transition by plotting a transition plot, where two identical columns record different genres, and we use arrows and magnitudes to denote the transition and its number between genres in two columns.

Study the pattern of the timing of changing genres by analyzing the quantiles of "major change" labels in each actor's career.

Answer "whether a hugely successful movie would impact an actor's changing decision" by defining an equation that measures the success of movies and thresholds them as the "treatment" of observational studies. Then, we calculate the proportion of the genres of these movies that appear afterward as outcomes.

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
