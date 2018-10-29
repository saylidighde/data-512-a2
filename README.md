# Bias in Data

## Goal

The goal of this project is to understand how bias is introduced in research through sources like training data and evaluation metrics. By merging datasets of Wikipedia articles on politicians and country populations and utilizing the ORES machine learning API, I analyzed the results to assess the number of country-wise political articles and their quality.

The final tables show:
1.  Highest and lowest ranked countries in terms of number of politician articles as a proportion of country population
2.  Highest and lowest ranked countries in terms of number of GA and FA-quality articles as a proportion of all articles about politicians from that country

## Data sources

The dataset of Wikipedia articles can be found [here](https://figshare.com/articles/Untitled_Item/5513449) 
The dataset of country-wise populations can be found [here](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0)

## Resources used

This analysis was prepared using Python 3.6.4 running in a Jupyter Notebook environment.
* Documentation for Python can be found here: https://docs.python.org/3.5/
* Documentation for Jupyter Notebook can be found here: http://jupyter-notebook.readthedocs.io/en/latest/

The following Python packages were used and their documentation can be found at the accompanying links:
* [Pandas](https://pandas.pydata.org/pandas-docs/stable/api.html): Data Analysis for Python
* [Requests](http://docs.python-requests.org/en/master/): HTTP for Humans

## ORES API 

I used Wikimedia API endpoint for a machine learning system called ORES to get quality scores for articles in the Wikipedia dataset. ORES assesses the quality of an article and assigns it to one of the following categories:

1. FA - Featured article
2. GA - Good article
3. B - B-class article
4. C - C-class article
5. Start - Start-class article
6. Stub - Stub-class article

*More information about these categories can be found [here](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment#Grades)
*More information about the ORES can be found [here](https://www.mediawiki.org/wiki/ORES)
*ORES API Documentation can be found [here](https://ores.wikimedia.org/v3/#!/scoring/get_v3_scores_context_revid_model)

A "high-quality" article belongs to either the FA or GA categories.

## Final data file

After obtaining ORES prediction for each of the articles in the Wikipedia dataset, this dataset was merged with the country population dataset. Rows found in one and not in the other were dropped. The final dataset after merging is saved in the [analyses_data.csv](https://github.com/saylidighde/data-512-a2/blob/master/analyses_data.csv) file.


## Expected Biases, Analysis Results, and Probable Explanations

In the table listing the highest-ranked countries in terms of the number of politician articles as a proportion of the country population, it was expected to find countries with low populations. Almost all the countries have a population lower than 0.1 million, except Iceland. It is also interesting to note that Iceland has 206 total articles, almost 4 to 5 times the articles of other countries on the list. I don't think this is a great metric to assess politician articles. Although it is expected that countries with higher populations will have more politicians and politician articles, the number of politician articles does not increase in a way to make a significant increase in the proportion of articles per population.

Again, in the table listing the lowest-ranked countries in terms of the number of politician articles as a proportion of the country population, it was expected to find countries with high populations. India and China, countries with the highest populations in the world, are on the list. All the countries on the list are also Non-English speaking countries and we are assessing data from the English Wikipedia. It is expected to have more political articles in native languages. So that may be a probable reason for the lower number of articles in English for Zambia, Uzbekistan, Mozambique, etc. 

In the table listing out the highest-ranked countries in terms of the number of high-quality articles as a proportion of all politician articles, finding North Korea and Saudi Arabia raises deep suspicions. Blatant human rights violations restrictions on media and freedom of speech are rampant in both. Mass population of North Korea does not even have internet access, let alone writing and editing articles on politicians. The extreme attention to detail to showcase such articles as high quality raises questions of the authors? identities and ulterior motives. The United States stands out in the list as a major powerful English-speaking country. Other major English speaking countries with dynamic political structures like Canada, Australia, and the UK are missing.

37 countries have 0 percent high-quality politician articles. Almost all of them are non-English speaking countries. That may be the reason for there not being any high-quality articles. Let alone high-quality articles, the number of total articles about politicians for many of them is much lower than the average of 250 articles per country. So the training data and metrics measured are probably too biased to take the results about the country-wise articles seriously.

## License

The project is licensed under the [MIT License](https://github.com/saylidighde/data-512-a2/blob/master/LICENSE).


