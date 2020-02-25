# Progress report

- Juan Berríos | jeb358@pitt.edu
- The purpose of this file is to document the progress I make on this project as the term progresses. It will contain a total of three reports (other than the preliminary one) by the end of term.<br/>
- **Table of contents**:
  - [Preliminary Report](##Preliminary-Report)
  - [1st progress report](##1st-progress-report)

## Preliminary report

- February 6, 2020.
- Repo created.
- Added `LICENSE.md`, `README.md`, `progress_report.md`, `project_plan.md`.
- Added `.gitignore` file for files that are not meant to be tracked as of now.

## 1st progress report

- February 25, 2020.
- Summary:
  - Over the last two weeks I worked on data acquisition as well as initial exploration and cleaning. I now have access to the complete data set thanks to the Department's license (shut out to Dr. Han). The first step was to take a general look at the data set. It comes in three formats and is organized in directories by country. I will use the lemmatized and POS-tagged format for my project. Files come in `txt` format and they are tab-delimited. Samples of the data that look just like the ones I am using are available at the [official website](https://www.corpusdata.org/formats.asp). I have also shared a copy in the data_samples directory of my repository. I have also documented my early corpus_processing efforts in a [Jupyter notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/corpus_processing.ipynb). Thus far, I have created a pipeline for loading the corpus directory for each country, extracting tab-delimited files from them and turn them into data frames, and clean the data from unneeded rows such as symbols or redacted information (replaced with '@' in the data set).
- Sharing plan:
  - I have shared a sample that is in exactly the same format as the licensed data set. I am only at liberty to share such a sample due to the nature of the license, but I think it is enough to (i) illustrate what the data looks like and (ii) run my code with it if somebody wishes to do so. If interested, members of the Department can also request access to the full data set.
- What there is left to do:
  - One of the challenges of working with the the data (and the format I chose in particular) is that it is very large. That's why I opted for building a pipeline first using only one of the directories. Now I have to put the rest of the diretories through it.
  - There are still two cleaning tasks which I expect to complete by the next progress report. First, removing classes to which the morphological pattern doesn't apply (I will probably use POS tags for this). Second, removing formerly diminutivized forms that have lexicalized. The latter will be more time-consuming, my plan is to use a list based on a dictionary of Spanish (writing code that removes forms found in such a list from the data frames).
  - I expect to start exploring the final data frame (i.e., all countries included).
