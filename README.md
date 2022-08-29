# NLU Evaluation Scripts
## Methodology
We evaluate Recall and F-scores on a small and large dataset based on the home automation bot dataset from [“Benchmarking Natural Language Understanding Services for Building Conversational Agents (2019)"](http://arxiv.org/abs/1903.05566). The data is [available on github](https://github.com/xliuhw/NLU-Evaluation-Data).

The benchmark was conducted between 28th July and 4th August 2022. 

The experiment settings were trained on a single-fold, with the test set kept as holdout dataset during the training phase.

Full predictions with its scores on the test dataset are sorted back to its Ground Truth and provided in the folder. 

Disclaimer: 
- Google Cloud AutoML:
   - The benchmark results is based on the confidence threshold that yields the best F1-Score.

## Small

640 Training Sentences - 10 Sentences per Intent

1076 Test Sentences

|            | Sprinklr | Google Cloud  | Azure Language Studio | AWS Comprehend |
|------------|----------|---------------|-----------------------|----------------|
| Recall     | 0.867    |   0.782       |    0.789              |     0.725      |
| F1 (Macro) | 0.870    |   0.799       |    0.789              |     0.700      |

### Example sentence on Small models
#### Query: is there anything i need to be aware of
#### Ground Truth: calendar_query
|               | Sprinklr       | Google Cloud    | Azure Language Studio | AWS Comprehend |
|---------------|----------------|-----------------|-----------------------|----------------|
| Intent (Pred) |calendar_query  |general_dontcare |    general_dontcare   | calendar_remove|
| Confidence    | 0.73           |   0.15          |    0.49               | 0.09           |

#### Query: is there an alarm at four am
#### Ground Truth: alarm_query
|               | Sprinklr       | Google Cloud    | Azure Language Studio | AWS Comprehend | 
|---------------|----------------|-----------------|-----------------------|----------------|
| Intent (Pred) |alarm_query     |alarm_set        |    alarm_set          | alarm_set      |
| Confidence    | 0.7            |   0.96          |    1.0                |   0.27         |

## Large

1908 Training Sentences - ~30 Sentences per Intent

5518 Test Sentences

|            | Sprinklr | Google Cloud  | Azure Language Studio | AWS Comprehend |
|------------|----------|---------------|-----------------------|----------------|
| Recall     | 0.901    |   0.836       |    0.860              |     0.876      |
| F1 (Macro) | 0.903    |   0.862       |    0.860              |     0.867      |

### Example sentence on Large models
#### Query: how many countries are in the European Union
#### Ground Truth: qa_factoid
|               | Sprinklr       | Google Cloud  | Azure Language Studio |   AWS Comprehend |
|---------------|----------------|---------------|-----------------------|------------------|
| Intent (Pred) | qa_factoid     |   qa_currency |    qa_maths           | general_quirky   |
| Confidence    | 0.72           |   0.42        |    0.34               | 0.30             |

#### Query: let's go through all pending reminders
#### Ground Truth: calendar_query

|               | Sprinklr       | Google Cloud  | Azure Language Studio |  AWS Comprehend |
|---------------|----------------|---------------|-----------------------|-----------------|
| Intent (Pred) |calendar_query  |calendar_remove|    general_quirky     | calendar_set    |
| Confidence    | 0.74           |   0.85        |    0.73               | 0.29            |
