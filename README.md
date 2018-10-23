# Bias in Data

**Name**: Havan Agrawal

## Goal

The goal of this project is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.

## Data Sources Used

To create these tables, we will draw from three data sources:
  1. [The Wikipedia English Article Dataset (within the category "Category:Politicians by nationality")](https://figshare.com/articles/Untitled_Item/5513449)  
  2. [Population Data by Country](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0)  

## Resources Used
This analysis was prepared using Python 3.5 running in a Jupyter Notebook environment.  
Documentation for Python can be found [here](https://docs.python.org/3.5/)   
Documentation for Jupyter Notebook can be found [here](http://jupyter-notebook.readthedocs.io/en/latest/)   

For predicting article quality, the [ORES API](https://www.mediawiki.org/wiki/ORES) was used.

The following Python packages were used and their documentation can be found at the accompanying links:
 * [pandas](https://pandas.pydata.org/pandas-docs/stable/api.html)

## Files Created

An intermediate file called [`article_quality.csv`](./data/article_quality.csv) is created, which contains the predicted quality of each article.

## Visualizations Created

## License

 * This assignment code is released under the [MIT License](./LICENSE).  
 * The Wikipedia English language articles data source is released under the CC-BY-SA 4.0 license.  
 * The population data is released under the ??? license.  
