# RMS Titanic

Michaela Fox 2025-01-30

-   [Grading Rubric](#grading-rubric)
    -   [Individual](#individual)
    -   [Submission](#submission)
-   [First Look](#first-look)
    -   [**q1** Perform a glimpse of `df_titanic`. What variables are in this dataset?](#q1-perform-a-glimpse-of-df_titanic-what-variables-are-in-this-dataset)
    -   [**q2** Skim the Wikipedia article on the RMS Titanic, and look for a total count of souls aboard. Compare against the total computed below. Are there any differences? Are those differences large or small? What might account for those differences?](#q2-skim-the-wikipedia-article-on-the-rms-titanic-and-look-for-a-total-count-of-souls-aboard-compare-against-the-total-computed-below-are-there-any-differences-are-those-differences-large-or-small-what-might-account-for-those-differences)
    -   [**q3** Create a plot showing the count of persons who *did* survive, along with aesthetics for `Class` and `Sex`. Document your observations below.](#q3-create-a-plot-showing-the-count-of-persons-who-did-survive-along-with-aesthetics-for-class-and-sex-document-your-observations-below)
-   [Deeper Look](#deeper-look)
    -   [**q4** Replicate your visual from q3, but display `Prop` in place of `n`. Document your observations, and note any new/different observations you make in comparison with q3. Is there anything *fishy* in your plot?](#q4-replicate-your-visual-from-q3-but-display-prop-in-place-of-n-document-your-observations-and-note-any-newdifferent-observations-you-make-in-comparison-with-q3-is-there-anything-fishy-in-your-plot)
    -   [**q5** Create a plot showing the group-proportion of occupants who *did* survive, along with aesthetics for `Class`, `Sex`, *and* `Age`. Document your observations below.](#q5-create-a-plot-showing-the-group-proportion-of-occupants-who-did-survive-along-with-aesthetics-for-class-sex-and-age-document-your-observations-below)
-   [Notes](#notes)

*Purpose*: Most datasets have at least a few variables. Part of our task in analyzing a dataset is to understand trends as they vary across these different variables. Unless we’re careful and thorough, we can easily miss these patterns. In this challenge you’ll analyze a dataset with a small number of categorical variables and try to find differences among the groups.

*Reading*: (Optional) [Wikipedia article](https://en.wikipedia.org/wiki/RMS_Titanic) on the RMS Titanic.

<!-- include-rubric -->

# Grading Rubric {#grading-rubric}

<!-- -------------------------------------------------- -->

Unlike exercises, **challenges will be graded**. The following rubrics define how you will be graded, both on an individual and team basis.

## Individual {#individual}

<!-- ------------------------- -->

| Category | Needs Improvement | Satisfactory |
|----|----|----|
| Effort | Some task **q**’s left unattempted | All task **q**’s attempted |
| Observed | Did not document observations, or observations incorrect | Documented correct observations based on analysis |
| Supported | Some observations not clearly supported by analysis | All observations clearly supported by analysis (table, graph, etc.) |
| Assessed | Observations include claims not supported by the data, or reflect a level of certainty not warranted by the data | Observations are appropriately qualified by the quality & relevance of the data and (in)conclusiveness of the support |
| Specified | Uses the phrase “more data are necessary” without clarification | Any statement that “more data are necessary” specifies which *specific* data are needed to answer what *specific* question |
| Code Styled | Violations of the [style guide](https://style.tidyverse.org/) hinder readability | Code sufficiently close to the [style guide](https://style.tidyverse.org/) |

## Submission {#submission}

<!-- ------------------------- -->

Make sure to commit both the challenge report (`report.md` file) and supporting files (`report_files/` folder) when you are done! Then submit a link to Canvas. **Your Challenge submission is not complete without all files uploaded to GitHub.**

``` r
library(tidyverse)
```

```         
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.4     ✔ readr     2.1.5
## ✔ forcats   1.0.0     ✔ stringr   1.5.1
## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
## ✔ purrr     1.0.2     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

``` r
df_titanic <- as_tibble(Titanic)
```

*Background*: The RMS Titanic sank on its maiden voyage in 1912; about 67% of its passengers died.

# First Look {#first-look}

<!-- -------------------------------------------------- -->

### **q1** Perform a glimpse of `df_titanic`. What variables are in this dataset?

``` r
## TASK: Perform a `glimpse` of df_titanic
glimpse(df_titanic)
```

```         
## Rows: 32
## Columns: 5
## $ Class    <chr> "1st", "2nd", "3rd", "Crew", "1st", "2nd", "3rd", "Crew", "1s…
## $ Sex      <chr> "Male", "Male", "Male", "Male", "Female", "Female", "Female",…
## $ Age      <chr> "Child", "Child", "Child", "Child", "Child", "Child", "Child"…
## $ Survived <chr> "No", "No", "No", "No", "No", "No", "No", "No", "No", "No", "…
## $ n        <dbl> 0, 0, 35, 0, 0, 0, 17, 0, 118, 154, 387, 670, 4, 13, 89, 3, 5…
```

``` r
head(df_titanic)
```

```         
## # A tibble: 6 × 5
##   Class Sex    Age   Survived     n
##   <chr> <chr>  <chr> <chr>    <dbl>
## 1 1st   Male   Child No           0
## 2 2nd   Male   Child No           0
## 3 3rd   Male   Child No          35
## 4 Crew  Male   Child No           0
## 5 1st   Female Child No           0
## 6 2nd   Female Child No           0
```

**Observations**:

-   Class, Sex, Age, Survived, n

### **q2** Skim the [Wikipedia article](https://en.wikipedia.org/wiki/RMS_Titanic) on the RMS Titanic, and look for a total count of souls aboard. Compare against the total computed below. Are there any differences? Are those differences large or small? What might account for those differences?

``` r
## NOTE: No need to edit! We'll cover how to
## do this calculation in a later exercise.
df_titanic %>% summarize(total = sum(n))
```

```         
## # A tibble: 1 × 1
##   total
##   <dbl>
## 1  2201
```

**Observations**:

-   Write your observations here
-   Are there any differences?
    -   Yes, there is a difference of about 23 people.
-   If yes, what might account for those differences?
    -   Wikipedia says that there was an *estimated* 2224 passengers. It could be possible that this number is slightly off.
    -   The data set might be older than the Wikipedia article, it is possible that some of the people aboard were not accounted for when it was created.

### **q3** Create a plot showing the count of persons who *did* survive, along with aesthetics for `Class` and `Sex`. Document your observations below.

*Note*: There are many ways to do this.

``` r
## TASK: Visualize counts against `Class` and `Sex`
df_titanic %>% 
  ggplot(aes(x = Survived, y = n, fill = Sex)) + 
  geom_col(position = "dodge") +
  facet_wrap(~ Class)
```

![](c01-titanic-assignment_files/figure-gfm/q3-task-1.png)<!-- -->

**Observations**:

-   There tended to be more females who survived than males.
-   The crew was majority male, which could explain why it is the only class where more men survived than women.
-   There were more males aboard the ship overall.

# Deeper Look {#deeper-look}

<!-- -------------------------------------------------- -->

Raw counts give us a sense of totals, but they are not as useful for understanding differences between groups. This is because the differences we see in counts could be due to either the relative size of the group OR differences in outcomes for those groups. To make comparisons between groups, we should also consider *proportions*.$$1$$

The following code computes proportions within each `Class, Sex, Age` group.

``` r
## NOTE: No need to edit! We'll cover how to
## do this calculation in a later exercise.
df_prop <-
  df_titanic %>%
  group_by(Class, Sex, Age) %>%
  mutate(
    Total = sum(n),
    Prop = n / Total
  ) %>%
  ungroup()
df_prop
```

```         
## # A tibble: 32 × 7
##    Class Sex    Age   Survived     n Total    Prop
##    <chr> <chr>  <chr> <chr>    <dbl> <dbl>   <dbl>
##  1 1st   Male   Child No           0     5   0    
##  2 2nd   Male   Child No           0    11   0    
##  3 3rd   Male   Child No          35    48   0.729
##  4 Crew  Male   Child No           0     0 NaN    
##  5 1st   Female Child No           0     1   0    
##  6 2nd   Female Child No           0    13   0    
##  7 3rd   Female Child No          17    31   0.548
##  8 Crew  Female Child No           0     0 NaN    
##  9 1st   Male   Adult No         118   175   0.674
## 10 2nd   Male   Adult No         154   168   0.917
## # ℹ 22 more rows
```

### **q4** Replicate your visual from q3, but display `Prop` in place of `n`. Document your observations, and note any new/different observations you make in comparison with q3. Is there anything *fishy* in your plot?

``` r
df_prop %>% 
  ggplot(aes(x = Survived, y = Prop, fill = Sex)) + 
  geom_col(position = "dodge", color = "black") +
  facet_wrap(~ Class)
```

```         
## Warning: Removed 4 rows containing missing values or values outside the scale range
## (`geom_col()`).
```

![](c01-titanic-assignment_files/figure-gfm/q4-task-1.png)<!-- -->

**Observations**:

-   Write your observations here.
    -   Instead of a whole number the values of prop are decimals from 0 to
        1.  
    -   It is more evident that the majority of people who survived were female.
-   Is there anything *fishy* going on in your plot?
    -   There is a warning that says 4 rows containing missing values/values outside the range were removed.
    -   It says 100% of people in first and second class survived.

### **q5** Create a plot showing the group-proportion of occupants who *did* survive, along with aesthetics for `Class`, `Sex`, *and* `Age`. Document your observations below.

*Hint*: Don’t forget that you can use `facet_grid` to help consider additional variables!

``` r
df_prop %>% 
  ggplot(aes(x = Survived, y = Prop, fill = Sex)) + 
  geom_col(position = "dodge") +
  facet_wrap(Age ~ Class)
```

```         
## Warning: Removed 4 rows containing missing values or values outside the scale range
## (`geom_col()`).
```

![](c01-titanic-assignment_files/figure-gfm/q5-task-1.png)<!-- -->

**Observations**:

-   All first and second class children survived.
-   Almost all first class women survived.
-   The majority of women survived.
-   There were no children part of the crew.
-   If you saw something *fishy* in q4 above, use your new plot to explain the fishy-ness.
    -   The plot from q4 did not distinguish between adults and children. Survival rates for children were significantly different from adults. The q4 plot had the survival rates for children and adults overlapping. Since both bars were the same color, they were indistinguishable, causing it to look like the same amount of children and adults survived.

# Notes {#notes}

<!-- -------------------------------------------------- -->

$$1$$ This is basically the same idea as [Dimensional Analysis](https://en.wikipedia.org/wiki/Dimensional_analysis); computing proportions is akin to non-dimensionalizing a quantity.
