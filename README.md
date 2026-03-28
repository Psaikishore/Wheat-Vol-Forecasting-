Here’s a more **natural, student-style README.md** — mixed paragraphs + bullets, less “perfect AI tone”, and more like something you’d actually submit:

---

# 📊 Volatility Forecasting of Wheat Futures

### Using Econometric and Deep Learning Models

## Overview

This project studies how to forecast volatility in wheat futures markets using a combination of traditional econometric models and deep learning techniques. The main idea was to see whether combining these two approaches (instead of using them separately) can lead to better predictions.

Volatility is an important quantity in financial markets because it directly affects risk management, derivative pricing, and trading strategies. Since commodity markets like wheat are influenced by many unpredictable factors (weather, geopolitics, supply-demand), modeling volatility becomes even more challenging and interesting.

---

## What this project does

In this project, I tried to approach the problem step-by-step:

* First, build **baseline econometric models** like GARCH, EGARCH, and EWMA
* Then, implement **deep learning models** such as RNNs and LSTMs
* Finally, create **hybrid models** by combining outputs of econometric models with neural networks

The goal was to compare all these approaches and figure out which one works best for forecasting volatility.

---

## Dataset

The dataset consists of daily wheat futures prices over a long time period.

* Time range: 1996 – 2025
* Around 7,800 observations
* Data used:

  * Wheat futures prices
  * Gold prices (as an external market indicator)
  * Global wheat production

Instead of using raw prices, I converted everything into **log returns**, since financial time series are usually non-stationary.

Some preprocessing steps included:

* Handling missing values (forward filling)
* Creating a continuous futures series
* Normalizing inputs for neural networks

---

## Models Used

### Econometric Models

These act as the baseline and are widely used in finance:

* GARCH(1,1) → captures volatility clustering
* EGARCH → handles asymmetry (positive vs negative shocks)
* EWMA → simple and commonly used in risk management

### Deep Learning Models

These are more flexible and can capture nonlinear patterns:

* Simple RNN
* LSTM (used mainly because it handles long-term dependencies better)

### Hybrid Models

This is the main part of the project.

* Added GARCH-type volatility estimates as inputs to neural networks
* Tried different combinations:

  * Single feature (e.g., GARCH + LSTM)
  * Two features (e.g., GARCH + EGARCH + LSTM)
  * All three combined

---

## Methodology

The workflow roughly looked like this:

* Convert prices → log returns
* Generate features like:

  * Absolute returns
  * Squared returns
  * Log of squared returns
* Define target as **22-day realized volatility**
* Split data into training and testing sets
* Train models and compare performance

---

## Evaluation

To compare models, I used multiple metrics:

* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
* HMAE and HMSE (scale-adjusted versions)

I also used statistical tests like:

* Diebold-Mariano test
* Wilcoxon signed-rank test

This was important to check whether differences in performance were actually significant.

---

## Results

A few key takeaways from the results:

* Hybrid models consistently performed better than both:

  * Pure econometric models
  * Pure deep learning models

* The best model was:

  * **LSTM + GARCH + EGARCH**

* Adding too many features didn’t always help → diminishing returns

* Classical models like GARCH worked reasonably well, but couldn’t match hybrid models

---

## Challenges

Some things that were harder than expected:

* Choosing the right **volatility target definition**
* Handling futures data (rollover issues, expiry effects)
* Preventing overfitting in neural networks
* Making fair comparisons across very different model types

---

## Conclusion

Overall, this project shows that combining econometric models with deep learning works better than using either one alone.

The hybrid approach benefits from:

* Structure and interpretability (from GARCH models)
* Flexibility and nonlinearity (from LSTMs)

This makes it a strong candidate for real-world volatility forecasting problems.

---

## Future Work

If I had more time, I would explore:

* Adding macroeconomic or weather data
* Trying Transformer-based models
* Applying the same framework to other commodities or equities

---
