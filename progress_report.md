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
  - Over the last two weeks I worked on data acquisition and initial exploration and cleaning. I now have access to the complete data set thanks to the [Department's](https://www.linguistics.pitt.edu/) license (shut out to [Dr. Han](https://github.com/naraehan)). The first step was to take a general look at the data set. It comes in three formats and is organized in directories by country. I will use the lemmatized and POS-tagged format for my project. Files come in `.txt` format and they are tab-delimited. Samples of the data that look just like the ones I am using are available at the [official website](https://www.corpusdata.org/formats.asp). I have also shared a copy in the [data_samples](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/tree/master/data_samples) directory of my repository. I have also documented corpus processing in a [Jupyter notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/corpus_processing.ipynb). Thus far, I have created a pipeline for loading the corpus directory for each country, extracting tab-delimited files from them and turn said files into data frames. I also removed unnecessary rows such as symbols or redacted information (replaced with '@' in the data set).
- Sharing plan:
  - I have shared a sample that is in exactly the same format as the licensed data set. I am only at liberty to share such a sample due to the nature of the data set's license, but I think it is enough to (i) illustrate what the data looks like and (ii) run my code with it if somebody wishes to do so. If interested, members of the Department can also request access to the full data set. As for my own license, I am currently deciding between an MIT license and a GNU license.
- What there is left to do:
  - One of the challenges of working with this data set (and the format I chose in particular) is that it is very large. That's why I opted for building a pipeline first using only one of the directories. Now I have to put the rest of the directories through it.
  - There are still two cleaning tasks which I expect to complete by the next progress report. First, removing classes to which the morphological pattern doesn't apply (I will probably use POS tags for this). Second, removing formerly diminutivized forms that have lexicalized. The latter will be more time-consuming, my plan is to use a list based on a dictionary of Spanish (writing code that removes forms found in such a list from the data frame).
  - I expect to start exploring the final data frame (i.e., all countries included).

  ## 2nd progress report

  - March 17, 2020.
  - Summary: at this stage I have completed the data acquisition process and I have also finished cleaning and reorganizing the data. For this purpose, I kept working on the existing [corpus processing notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/corpus_processing.ipynb), put every directory (i.e., each country) through the pipeline, and saved the results as pickled files. Once I was done with that task, I created a [new (continuing) notebook](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/code/cleaning_analysis.ipynb) to finish removing extraneous rows and started analyzing the data. I also refined the part of speech column and created some new columns that might be useful for linguistic analysis. There is a total of 20 individual data frames (by country) and one master data frame. I also made minor changes to the [`README.md`](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/README.md) file and added a [license](https://github.com/Data-Science-for-Linguists-2020/Diminutive-Suffix-Productivity/blob/master/LICENSE.md) to the repository (more on this below).
  - Sharing scheme: this part of my project was completed by the last progress report. Following some of the suggestions I received, I also added a subset of the sample that can be viewed online in case the user is not able or does not wish to download the full sample as a zip file. Given the license of the data set that I am using I have to keep my `/data` folder private, but within that folder I should also note that I created a `/pickle` folder for ease of access.
  - Licensing: I have decided to use a [GNU General Public License v3.0](https://choosealicense.com/licenses/gpl-3.0/). I wanted to use a flexible, relatively straightforward license, which is why I was considering a GNU license and an MIT license. I opted for the former because I care about improvements being shared and because I would prefer that derivations of my work are shared under the same license.
