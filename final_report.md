# Final report

- Juan Berríos | jeb358@pitt.edu

- **Table of contents**:
  - [1. Introduction](#1-Introduction)
  - [2. Background](#2-Background)
  - [3. Research questions and hypotheses](#3-Research-questions-and-hypotheses)
  - [4. History and process](#4-History-and-process)
  - [5. Exploration](#5-Exploration)
  - [6. Analysis](#6-Analysis)
  - [References](#References)

## 1. Introduction
The purpose of this project is to do a cross-dialectal analysis of two competing Spanish diminutive suffixes (<i>-ito</i>, <i>-illo</i>) in terms of productivity; i.e., the extent to which a morphological pattern can be applied to new bases and form new words. In this analysis I also consider dialectal variation, given that the data might not necessarily indicate the same trends for all varieties of Spanish. The main goals are the following:

1. Explore the cross-dialectal distribution of two competing diminutive suffixes in a representative, cross-dialectal corpus.
2. Apply statistical measures of productivity (Baayen, 20009) to the data.
3. Determine whether differences are reflected across varieties.

## 2. Background

The function of diminutive suffixes is to form a complex word denoting a smaller version of the base (Haspelmath & Sims, 2010). In Spanish, diminutive formation is a robust process attested in all varieties, and it applies widely to nouns and adjectives, as well to a limited set of adverbs and gerunds.

The other anchor of this project are statistical measures of productivity (Baayen, 2009), which are explained below:

1. Realized productivity: the size of the morphological category, as measured by the type count of the members of a morphological category in a corpus with N tokens.
2. Expanding productivity: the rate at which a category is attracting new members, as measured by the number of words in a morphological category that occur only once in a corpus of N tokens; the hapax legomena.
3. Potential productivity: the number of occasionalisms. A category that can produce a higher number of occasionalisms is thought to be productive. This is measured by the number of hapax legomena exhibiting a pattern divided by the total number of tokens exhibiting the same pattern. Also known as the category-conditioned degree of productivity or Baayen's *P*. A drawback of this measure is that it is sensitive to corpus size, which is why an alternative, the hapax-conditioned degree of productivity or *P**, is also used.  This is measured by the number of hapax legomena exhibiting a pattern divided by the total number of hapax legomena (exhibiting any pattern) in the corpus. For both measures, the higher the resulting number, the higher the productivity. When presenting results, it is standard for both *P* and *P** to be multiplied by 100.

## 3. Research questions and hypotheses

The research questions that guided my exploration and analysis were the following:

1. What is the productivity of each suffix?
2. Are the differences statistically significant?
3. Are differences reflected across varieties?

For the first question, I hypothesized that <i>-ito</i> would be more productive across all metrics following prior descriptive work. With regard to the second question, I hypothesized that differences would be reflected in statistical measures of productivity. Lastly, for question three I hypothesized that there would be differences when examining the data by variety given that <>-illo</i> is claimed to be productive in Peninsular Spanish.

## 4. History and process

Found data, add value, follow best data practices
My found data comes from the [<i>Corpus del español</i>](https://www.corpusdelespanol.org/), which is a cross-dialectal corpus created in 2016 and totaling 2 billion words. 21 Spanish-speaking countries represented in the corpus. The corpus is searchable online and the full data set, which is fully lemmatized and POS-tagged, is available with a license. The data set is available in three formats: (i) Database (Structured Query Language), (ii) Word/lemma/PoS, and (iii) linear (raw) text. All are .txt files and the former two are tab-delimited. I used the second format due to its compatibility with the Pandas data frame structure. The three main challenges I faced when working with this data set were its size (around 70 GB when uncompressed), the structure of directories, and the extraction of relevant rows for my analysis.

In the [first notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/corpus_processing.ipynb) I took care of corpus processing. For this purpose, I created a set of functions that would loop through each directory (one for each country) and create data frame objects that contained only rows ending in the segments of interest. I also created a list of hapax legomena found in each subset of the corpus since I need that to compute statistical measures of productivity. I kept the code as streamlined as possible but did use one cell for each country given the memory limitations of my computer. If I were to submit the script as a `.slurm` job I would condense the script further with another definite loop.

In the [second notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/cleaning_exploratory_analysis.ipynb) I focused on cleaning efforts and exploratory analysis. I created a master_DF object including all varieties and refined the POS column to removed syntactic categories to which the morphological pattern does not apply.  The problem, however, was that there were still many tokens that did not belong in the data frame because they are (i) lexicalized forms that have acquired a meaning of their own, or (ii) words that meet the word class and phonological requirement but simply do not happen to be diminutives. Based on my knowledge of the topic, the forms I want to remove are much more frequent than diminutivized forms. It follows that if I extract a list of highly frequent forms from the corpus that end in the segments of interest I can get a list that I can later cross-compare with my data frame's `Lemma` column. Coincidentally, the corpus offers a useful resource for this purpose; that is, a lexicon. I loaded it, derived a frequency-based list of lemmas exclude from it, and then actually excluded those from the `master_DF` object. Having done this, the vast majority of extraneous rows are removed (there are still some left in the data frame that I would have to remove manually, but given their low frequency and the size of data set I do not think those should affect analysis at all).

In the [last notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/statistics_analysis.ipynb), devoted to statistics and analysis, I extracted hapax legomena from the master data frame and created new summary data frame objects including token counts, type counts, hapax legomena counts, P, and P* for the whole data set and for each variety. Finally, I plotted differences across and within varieties.

## 5. Exploration

The following are visualizations of the distribution of the data. You can find tables providing specific figures for each diminutive by POS and variety in [the cleaning and exploratory analysis notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/cleaning_exploratory_analysis.ipynb).

<img src="../figures/1_diminutive.png" alt="Figure 1" width="400">

Figure 1 above illustrates the token counts for each diminutive across the entire data set. As expected, <i>-ito</i> is far more numerous. Its X tokens account for X% of the data, as compared to X tokens (X%) <i>-illo</i>. Token counts, however, are only useful for a preliminary estimation of differences in size given that productivity can vary chronologically and a category with a high token count (e.g., <i>-ment</i> in English) might me mostly unproductive in the present day. It is, nevertheless, a good point of departure.

<img src="../figures/2_diminutive_POS.png" width="400">

Figure 2 above illustrates the ratio of diminutive suffix by POS. I use ratios rather than counts for this plot and the following given the imbalance between categories. It appears that there's a bigger gap in usage depending on the token's category. <i>-illo</i> appears to be less common with adjectives. For nouns, the proportion amounts to 18% of the tokens, whereas for adjectives it is only 8%.

Lastly and most importantly, the ratio of diminutive suffixes used by variety. Below is a reminder of the varieties considered in the order that they appear followed by the plot:

* Argentina: AR
* Bolivia: BO
* Chile: CL
* Colombia: CO
* Costa Rica: CR
* Cuba: CU
* Dominican Republic: DO
* Ecuador: EC
* Spain: ES
* Guatemala: GT
* Honduras: HN
* Mexico: MX
* Nicaragua: NI
* Panama: PA
* Peru: PR
* Puerto Rico: PR
* Paraguay: PY
* El Salvador: SV
* United States: US
* Uruguay: UY

<img src="../figures/3_diminutive_variety.png" alt="Figure 1" width="800">

As can be seen in the chart, the ratio is similar for most countries other than Spain and (interestingly) Costa Rica, which are the only varieties where <i>-illo</i> eclipses the 20% threshold (21 and 23%, respectively). I expected the result for Spain given that in descriptive work it is claimed that the suffix is more common there, but I did not expect Costa Rica not only to have a similar rate but actually surpass. Again, since these ratios are based on tokens, caution must be used, but it is one of the first surprising results.

## 6. Analysis

I will now start with an analysis proper, focused on statistical measures of productivity. To begin, the table below summarizes statistics for the entire data set. You can also find the same figures by variety in the [statistics and analysis notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/statistics_analysis.ipynb).

|   Diminutive  |   Tokens      |    Types    |    Hapax    |    <i>P</i>   |    <i>P*</i>   |
|---------------|---------------|-------------|-------------|---------------|----------------|
| <i>-illo</i>  |    233202     |    13157    |    6513     |    2.79286    |    0.121974    |
| <i>-ito</i>   |    1195810    |    48930    |    26611    |    2.22535    |    0.498367    |

1. Realized productivity: as indicated by the type count, <i>-ito</i> is the larger category out of the two considered. This is visualized in Figure 4 below.

<img src="../figures/4_types_across_varieties.png" alt="Figure 1" width="400">

2. Expanding productivity: as indicated by the hapax legomena count, <i>-ito</i> is attracting more members than <i>illo</i>. This is visualized in Figure 5 below.

<img src="../figures/5_hapax_across_varieties.png" alt="Figure 1" width="400">

3. Potential productivity: as measured by the category-conditioned degree of productivity (*P*) or the hapax-conditioned degree of productivity (*P**). The category-conditioned degree of productivity doesn't appear to fully capture the difference between these two suffixes in terms of occasionalisms, given that both suffixes appear to have around the same standing with <i>-illo</i> showing a slight advantage. This might be due to the fact that <i>-illo</i> has notoriously fewer tokens, so the comparison is not completely fair. Alternatively, the hapax-conditioned degree of productivity shows a far more noticeable difference, with <i>-illo</i> having a score that is fourth times larger than that of <i>-ito</i>.

Lastly, Figures 6 and 7 below illustrate the category-conditioned and hapax-conditioned degree of productivity by variety. Given that varieties are only being compared to themselves, the bars are parallel to each other; i.e., they are not affected by imbalances in corpus size.

<img src="../figures/6_category_contioned_productivity.png" alt="Figure 1" width="800">

<img src="../figures/7_hapax_contioned_productivity.png" alt="Figure 1" width="800">

Within varieties, the numbers appear to follow the same trend as those of the master data frame. A few differences are worth noting, however.  Whereas <i>P</i> above showed both suffixes in similar standing, the differences here are higher in favor <i>-illo</i>, particularly in countries such as Peru where it almost doubles <i>-ito</i>. For <i>P*</i>, however, <i>-ito</i> remains the prevailing suffix in all varieties, although differences vary by country and might worth looking at with inferential statistics.

To summarize and in responses to my research questions:

1. The results of my analysis indicate that, in terms of distribution, <i>-ito</i> is the larger morphological category as shown by the token, type, and hapax legomena counts not only at the cross-dialectal level but also zooming in on each country. I believe the results are important because to the best of my knowledge there aren't numbers to back claims that have been made in the literature about the prevalence of each suffix and because the same model can be replicated for other competing morphological patterns.
2. When turning to statistical measures of productivity, a surprising result is that the category conditioned degree of productivity shows both suffixes at the same standing. A caveat of such a measure is corpus size, which is important to consider in this project given that the subsets by variety vary widely in size, with Spain's being by far the largest. Given the uniformity of the results when using the hapax-conditioned degree of productivity, I would argue that it is a better gauge of the synchronic productivity of a morphological pattern, especially when there are imbalances in the data.
3. Lastly and of particular importance for morphological theory, the results show that although the by-variety trends generally mirror those seen cross-dialectally, there are exceptions noticeable upon closer inspection. In Spain and Costa Rica, for instance both raw counts and statistical measures indicate an (unexpected for the latter) higher prevalence of <i>-illo</i>. Productivity hence might be affected not only by system-internal factors but also system-external factors. In a future iteration of this project, what I would like to do is to examine the difference using regression models (mixed-effects logistic regressions, for instance) and, on the more theoretical side, to explore what diachronic research has to say regarding the evolution of these suffixes in general but in particular in the varieties where it appears to go against cross-dialectal trends.

## References

Baayen, H. (2009). Corpus linguistics in morphology: morphological productivity. In A. Lüdeling & M. Kyto (Eds.), <i>Corpus Linguistics. An international handbook</i> (pp. 900-919). Berlin: Mouton De Gruyter.

Davies, Mark. (2016). <i>Corpus del español</i> [online corpus]. Retrieved from 〈https://www.corpusdelespanol.org〉 (28 January, 2020).

Haspelmath, M., & Sims, A. D. (2010). <i>Understanding morphology</i> (2nd ed.). London, UK: Hatchette.
