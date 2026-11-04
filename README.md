# Ames Housing Price Regression

Our team's entry for the NYU Stern Data Bootcamp Kaggle challenge: predict what houses in Ames, Iowa sold for. Everything is built with scikit-learn.

**Team:** Sacha Bidermann, Charlie Chen, Harry Chen

The full walkthrough is in [BestModel.ipynb](BestModel.ipynb) ([open in Colab](https://colab.research.google.com/github/sachabidermann/ames-housing-regression/blob/main/BestModel.ipynb)).

## What we did

We started with the dumbest possible guess, the average price for every house, and it was off by about $78k. Anything we built had to beat that.

From there we tried three things:

- **A small linear regression** with the features we figured matter most:  quality, living area, basement size, garage, year built, year remodeled, bathrooms, plus neighborhood, kitchen quality and exterior quality.
- **A bigger linear regression** with 24 features instead of 10.
- **KNN** on the small feature set, testing k from 1 to 20. k = 7 did best.

We held back 25% of the training data to score each:

| Model | Error (RMSE) |
|---|---|
| Average price | $78,120 |
| Small linear | $28,583 |
| KNN (k = 7) | $28,439 |
| **Big linear** | **$26,351** |

## Final model

The big linear regression won, so we submitted that. We had two changes, though:

1. We dropped the few houses over 4,000 sq ft before training. There are a couple, and they drag the line off.
2. If a test house is bigger than everything else in the training data, we don't trust the line that far out. That house gets the price of its closest match instead.

## Running it

Open the notebook in Colab, upload the class `ames.zip`, and run all cells. It gives the `preds.csv` for Kaggle. The data isn't in this repo.
