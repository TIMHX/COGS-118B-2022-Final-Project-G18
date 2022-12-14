<h1 align="center">
  Transformers for Sentiment Analysis on Financial Text
</h1>

<h4 align="center">
  Fine-tuned Models based on pretrained Hugging Face Transformers <br />
  Xing Hong, Xiangyi Kong
</h4>

## Data Links:
- Tweets: 
1. https://ieee-dataport.org/open-access/stock-market-tweets-data (only the manual labelled)
2. https://www.kaggle.com/datasets/yash612/stockmarket-sentiment-dataset

- Financial News (all data)

https://www.researchgate.net/publication/251231364_FinancialPhraseBank-v10

same as

https://www.kaggle.com/datasets/ankurzing/sentiment-analysis-for-financial-news?resource=download


## Usage

### From Command Line
```bash
# this will install necessary packages
pip install -r requirements.txt

# this will run the whole pipeline consists of downloading full dataset, generate data, 
# downloading our finetuned models from google drive, unzip model folders, trainning process for new model,
# predict sentiments on testing dataset

run python3 run.py generate_data download_models train test

# for default testing run , no argument needed
# test run will download, unzip our finetuned models from google drive,
# predict on dummy testdata(3 samples) and output predicted labels

run python3 run.py
```

### File structure and configuration
All configuration will be read from config folder, **data-params.yml** will be read when generating data, **model_config.yml** will be read when downloading, unzipping finetuned models, **train-params.yml** will be read as training hyperparameters as well as io path, **test-params.yml** consists io for test dataset and testrun dummy dataset.

Raw dataset will be scraped from data sources and saved in data/raw, processed data will be saved in data/temp predictions will be saved in data/out, all datafiles will be saved in .csv file.

Finetuned models, no matter directly output from training process, or download from google shared drive, all will be saved in results folder **train.py** will download pretrained models from Hugging Face hub, and read data from data/temp, finally save finetuned model to result folder.

**test.py** will take two argument, test_target and test_lines. test_target can be specified as test, which will generate prediction on testing data
or default as testdata to predict on testrun dummy data. All prediction will be saved in data/out

