# Bias in Data

## Goal

The goal of this project is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.

## Data Sources Used

To create these tables, we will draw from two data sources:
  1. [The Wikipedia English Article Dataset (within the category "Category:Politicians by nationality")](https://figshare.com/articles/Untitled_Item/5513449)  
  2. [Population Data by Country](https://www.dropbox.com/s/5u7sy1xt7g0oi2c/WPDS_2018_data.csv?dl=0)  

### Data Descriptions/Schemas

#### The Wikipedia Dataset

| Column | Description |
|--------|-------------|
| page | The title of the page |
| country | The country of the political entity |
| rev_id | The revision ID |

#### The Population Dataset

| Column | Description |
|--------|-------------|
| Geography | The name of the geographical entity (not necessarily a country) |
| Population mid-2018 (millions) | Population of the geographical region in millions, as of 2018 |

#### Article Quality (Intermediate file)

| Column | Description |
|--------|-------------|
| rev_id | The revision ID |
| prediction | One of "B", "C", "Start", "Stub", "FA" or "GA" [(see below)](#ores) |

## Resources Used

### Versions and Documentation
 * This analysis was prepared using Python 3.7 running in a Jupyter Notebook environment.  
 * Documentation for Python can be found [here](https://docs.python.org/3.5/)   
 * Documentation for Jupyter Notebook can be found [here](http://jupyter-notebook.readthedocs.io/en/latest/)   

### <a name="ores"></a> ORES
For predicting article quality, the [ORES API](https://www.mediawiki.org/wiki/ORES) was used. The prediction returned by ORES is in the form of probabilities, as well as an absolute prediction. An article may be predicted to have one of the following quality levels:
 * **FA** - Featured article
 * **GA** - Good article
 * **B** - B-class article
 * **C** - C-class article
 * **Start** - Start-class article
 * **Stub** - Stub-class article

We define "high-quality" as an article predicted to be either **FA** or **GA**.

A sample response from ORES looks like this:
```json
{
  "enwiki": {
    "models": {
      "wp10": {
        "version": "0.5.0"
      }
    },
    "scores": {
      "757539710": {
        "wp10": {
          "score": {
            "prediction": "Start",
            "probability": {
              "B": 0.0950995993086368,
              "C": 0.1709859524092081,
              "FA": 0.002534267983331672,
              "GA": 0.005731369423122624,
              "Start": 0.7091352495053856,
              "Stub": 0.01651356137031511
            }
          }
        }
      },
      "783381498": {
        "wp10": {
          "score": {
            "prediction": "Start",
            "probability": {
              "B": 0.020202281665235494,
              "C": 0.040498863202895134,
              "FA": 0.002648428776337411,
              "GA": 0.005101906528059532,
              "Start": 0.4793812253273645,
              "Stub": 0.452167294500108
            }
          }
        }
      }
    }
  }
}
```

### Python Packages
The following Python packages were used and their documentation can be found at the accompanying links:
 * [pandas](https://pandas.pydata.org/pandas-docs/stable/api.html): Python Data Analysis Library
 * [tqdm](https://github.com/tqdm/tqdm): Fast and Extensible Progress Bar
 * [requests](http://docs.python-requests.org/en/master/): HTTP for Humans

## Files Created

An intermediate file called [`article_quality.csv`](./data/article_quality.csv) is created, which contains the predicted quality of each article.

## Reproducibility

In order to reproduce the results in this notebook, follow the following steps:

1. Clone this repository:
```
git clone https://github.com/havanagrawal/data-512-a2.git
```
2. (Optional) Create and activate a virtual environment using `virtualenv`:
```
virtualenv hcds-a2
. hcds-a2/bin/activate.sh
```
3. Install external libraries using pip (or conda)
```
pip3 install pandas requests tqdm
```
4. Start the Jupyter notebook:
```
jupyter notebook
```
5. To observe the exact same results as this notebook, simply rerun it in Jupyter. To retrieve fresh predictions from ORES, delete (or rename) the [`article_quality.csv`](./data/article_quality.csv) file

## License

 * This assignment code is released under the [MIT License](./LICENSE).  
 * The Wikipedia English language articles data source is released under the CC-BY-SA 4.0 license.  
 * The population data is released under the ??? license.  
