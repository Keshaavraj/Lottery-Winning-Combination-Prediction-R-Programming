# Lottery Winning Combination Prediction

This repository contains code for predicting winning combinations for lottery tickets using association rule mining techniques implemented in R with the arules package.

## Objective 🎯
The objective of this project is to analyze transaction data from lottery tickets and identify association rules that can help predict winning combinations. By mining these rules, we aim to uncover patterns and relationships among ticket numbers to enhance the chances of selecting winning combinations in future lottery draws.

## Getting Started 🚀
To get started with this project, you'll need to have R installed on your system. You can download R from the [official R website](https://www.r-project.org/). Additionally, you'll need to install the arules package, which can be done by running the following command in your R console:

```R
install.packages("arules")
```

## Usage ℹ️
**Data Preparation:** Ensure you have the Mahzooz.csv file containing your lottery ticket data. If not, replace it with your own dataset. Make sure the data is in CSV format and contains the transaction information of lottery tickets.

**Code Execution:**
- **Library Import:** This line imports the arules package, which provides functions for association rule mining in R.
```R
library(arules)
```
- **Data Reading:** This line reads the transaction data from the CSV file named "Mahzooz.csv". Each row in the CSV represents a transaction, and each item in a transaction is separated by a comma (,). The read.transactions function creates a transaction object k from the CSV data.
```R
k=read.transactions("Mahzooz.csv",sep = ",")
```
- **Dataset Dimensions:** This line calculates the dimensions of the transaction dataset k, showing the number of transactions and unique items.
```R
dim(k)
```
- **Transaction Inspection:** This line inspects the first 10 transactions in the dataset k, displaying the items purchased in each transaction.
```R
inspect(k[1:10])
```
- **Association Rule Mining:** This line applies the Apriori algorithm to mine association rules from the transaction data k. It specifies minimum support (supp) and minimum confidence (conf) thresholds for generating the rules.
```R
rules=apriori(k,list(supp=0.08,conf=0.9))
```
- **Sorting Rules:** This line sorts the generated association rules based on the lift metric in descending order, from highest to lowest.
```R
rules_sort=sort(rules, by='lift',decreasing=TRUE)
```
- **Rule Inspection:** This line inspects the sorted association rules, displaying their antecedents, consequents, support, confidence, lift, and count.
```R
inspect(rules_sort)
```
- **Parameter Adjustment and Re-run:** This line recalculates association rules with a lower minimum support threshold (0.03) while keeping the minimum confidence threshold at 0.9.
```R
rules=apriori(k,list(supp=0.03,conf=0.9))
```

## Findings 🔍
- **Dataset Dimensions:** The dataset consists of 36 transactions and 50 unique items.
- **Association Rules:** After mining association rules, the top rules based on lift were identified, revealing significant associations between certain numbers.
- **Rule Metrics:** Rules were evaluated based on support, confidence, coverage, and lift to determine their strength and relevance.

## Conclusions 📝
Through association rule mining, we were able to identify patterns and associations within the lottery ticket data. These findings can potentially assist lottery players in selecting numbers with higher probabilities of winning. By adjusting the support and confidence thresholds, we can refine the rules to improve their accuracy and applicability.
