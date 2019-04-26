# Project Overview

The final team project for EECS 486

github url: https://github.com/bryce-s/final_project

Training Steps:

- Fetch Article
- Generate Sentiment
- Get Stock Movement
- Assign += 1

## Module Diagram
It's still readable. Meagan disapproves, -4
![alt text](https://i.imgur.com/rArxpK4.png "Logo Title Text 1")

## Quickstart

Start server on Port 8080

```bash
python3 server/app.py
```

Start Front End on Port 3000

```bash
npm run start
```

## Fetching Articles

The application will target a small number of
news sources to train data and make predictions.
sources: http://www.marketwatch.com/rss/topstories

```
{
  "1": {
    "ticker": "APPL",
    "news_source": "WSJ"
    "title": "airplay flails again, good work APPL smh",
    "date": "2029-09-11T00:00:00.000Z"
  },
  "2": {
    "ticker": FB
    "news_source": "MarketWatch",
    "title": "Facebook buys a llama",
    "date": "2029-09-11T00:00:00.000Z"
  }
}
```

## Get Stock Movment

Compare date stock price withstock price at some future time (how do we define this? Maybe a week or day)

- time to compare (in the future) should be a parameter to this module! 

./get_stock_movement time_to_compare

```
  "1": {
    "ticker": "APPL",
    "news_source": "WSJ"
    "title": "airplay flails again, good work APPL smh",
    "date": "2029-09-11T00:00:00.000Z"
  },
  "2": {
    "ticker": FB
    "news_source": "MarketWatch",
    "title": "Facebook buys a llama",
    "date": "2029-09-11T00:00:00.000Z"
  }
}
```


## Sentiment Prediction
We take in article, ticker and news company name.
We return either a positive or negative sentiment prediction.


```
{
  "1": {
    "ticker": "APPL",
    "news_source": "WSJ"
    "sentiment_result": 1,
    "date": "2029-09-11T00:00:00.000Z"
  },
  "2": {
    "ticker": FB
    "news_source": "MarketWatch",
    "sentiment_result": -1,
    "date": "2029-09-11T00:00:00.000Z"
  }
}
```
## Classifier

Here, we're just checking if out prediction was correct.

update news_source -> score map; we don't necessarily need 
to communicate w. json here.

```
{
  "1": {
    "news_source": "WSJ"
    "prediction_correct": 1,
  },
  "2": {
    "news_source": "MarketWatch",
    "prediction_correct": -1,
  }
}
```


## Predictor

Probably in same program as classifer. Use score accuracy to resolve sentiment.
Take in a fresh news source and one of our predetermined tickers, just return our prediction for the ticker.

```
{
  "1": {
    "ticker": "APPL",
    "news_source": "WSJ",
    "recommend_buy": 1
  },
  "2": {
    "ticker": "MSFT", 
    "news_source": "MarketWatch",
    "recomemnd_buy": -1
  }
}
```
