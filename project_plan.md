# Diminutive suffix productivity in Spanish

- Table of contents:
  - [1. Data](#1-Data)
  - [2. Analysis](#2-Analysis)
  - [3. Presentation](#3-Presentation)

## Summary

- There are competing, semantically equivalent suffixes that can be used in Spanish (*-ito*, *-illo*), but they vary a great deal in productivity because of word-formation restrictions and dialectal variation. In this project I examine how informative statistical measures of productivity are using such suffixes as a test case. Besides morphology, I am also interested in dialectal variation, so an additional goal of this analysis is to determine whether patterns seen at the cross-dialectal level also hold when zooming in on a particular variety. My plan is to do an analysis using tokens drawn from a [large-scale, cross-dialectal corpus](https://www.corpusdelespanol.org/) and incorporating statistical measures such as Baayen's *P*.

## 1. Data
- For the purposes of this project I will be mainly working with data frames. Each data point will represent one use of a diminutivized word form. As of now, the columns I plan to include are: suffix, word form, lemma, concordance, grammatical gender, number, genre (blog, newspaper, etc.), and variety (country).
- Data source: [Corpus del Español Web/Dialects](https://www.corpusdelespanol.org/web-dial/).
  - A 2-billion word, POS-tagged corpus that covers all Spanish-speaking countries. It has an online interface but the full data set is only available upon purchase. You can download a file that contains 1% of the corpus as a sample, which is what I will use initially for exploration. Fortunately, the RHLMC has acquired a license so I expect to use the full corpus for the next stage.  
  - This is the most appropriate corpus to use for a project such as this because it's fully tagged and because it's the only one that can yield token counts large enough to run powerful statistical tests. It also covers all varieties, which is important for the purposes of this project.
- Data cleaning: the project will involve a great deal of data cleaning for two reasons. First, some of the forms end in the same segments but are not diminutives (e.g., *bonito* “pretty”).  Second, some forms have lexicalized and acquired a meaning of their own, so it is justified to exclude them from the analysis.

## 2. Analysis
- My end goal is to measure the productivity of the suffixes and hence provide quantitative support to the descriptive claims that have been made in the literature. More broadly, I am interested in testing the empirical validity of statistical measurements of productivity that have been mostly used for English.
  -  Measures of realized, expanding, and potential productivity [(Baayen, 2009)](https://www.degruyter.com/view/books/9783110213881.2/9783110213881.2.899/9783110213881.2.899.xml). These measures are useful because they allow us to quantify how productive a morphological pattern is, assuming the view that productivity is a matter of gradience rather than a contrast between productive and unproductive categories.
- Three questions:
  - What is the productivity of each suffix?
    - H1: *-ito* is claimed to be the more productive suffix by far. I expect this to be reflected in the data.
  - Are the differences statiscally signicant?
    - H2: I also expect differences, particularly those of potential productivity, to be significant.
  - Are differences reflected across variaties?
    - H3: one of the suffixes (*-illo*) is claimed to be more productive in Spain.
- As of now I plan to use regression models.
- If time allows:
  - I focus on this set of suffixes because (i) they are attested across varieties and (ii) token counts are likely to be high enough to make comparisons, but the analysis could be expanded to encompass less common suffixes (e.g., *-ico*) and augmentatives as well (e.g., *-azo*).

## 3. Presentation
- I plan to use plots to illustrate the distribution of the data as well as the differences between the subsets thereof.
- If time allows:
  - I would also like to explore packages to manipulate and visualize  spatial or geographic data.
