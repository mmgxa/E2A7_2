# E2A7_2

# Part 1 - QA Pair

## Loading Data

The file `Question_Answer_Dataset_v1.2.tar.gz` was used. After extracting, the `question_answer_pairs.txt` file in the `S08`, `S09`, and `S10` folders was used.

## Parsing Files
The `pd.read_csv` method was used (with ` sep="\t"`) to read the files. Unfortunately, the file for 2010 was giving an error, so as suggested on [StackOverflow](https://stackoverflow.com/questions/55010807/pandas-errors-parsererror-expected-after), the ` error_bad_lines=False` argument was used

Only the Question and Answer columns were retained.

Also, there were some missing values (Q and A) so those rows were removed using the `pd.dropna` method


## String Reversal

Reversing the input string (as done in the class) improved the results - loss was slighlty less than without reversing string

## Metric
The Accuracy metric cannot be used. Instead, perplexity - which is the exponent of the loss value - is recorded.

## Model
The same model that was presented in the class has been used to train and evaluate (including teacher-forcing for the former)

## Results



#### Training Log
|    epoch    |   Train PPL |  Train Loss |   Valid PPL |  Valid Loss |
| ----------- | ----------- | ----------- | ----------- | ----------- | 
|           1 |      332.43 |      5.8064 |      198.24 |      5.2895 |
|           2 |      167.47 |      5.1208 |      205.08 |      5.3234 |
|           3 |      140.73 |      4.9468 |      212.57 |      5.3593 |
|           4 |      125.51 |      4.8324 |      225.54 |      5.4185 |
|           5 |      116.91 |      4.7614 |      235.11 |      5.4601 |
|           6 |      108.79 |      4.6894 |      248.89 |       5.517 |
|           7 |      97.068 |      4.5754 |      254.31 |      5.5386 |
|           8 |      85.776 |      4.4517 |      259.73 |      5.5597 |
|           9 |      80.453 |      4.3877 |      260.74 |      5.5635 |
|          10 |       71.66 |      4.2719 |      278.31 |      5.6287 |
|          11 |       61.27 |      4.1153 |      286.99 |      5.6594 |
|          12 |       53.81 |      3.9855 |      290.56 |      5.6718 |
|          13 |      47.309 |      3.8567 |      301.51 |      5.7088 |
|          14 |       41.47 |       3.725 |       299.5 |      5.7021 |
|          15 |      34.464 |      3.5399 |      317.75 |      5.7613 |
|          16 |      29.699 |      3.3911 |      335.63 |       5.816 |
|          17 |      25.429 |      3.2359 |       354.8 |      5.8716 |
|          18 |      21.749 |      3.0796 |      352.79 |      5.8659 |
|          19 |      18.595 |      2.9229 |      359.44 |      5.8845 |
|          20 |      15.931 |      2.7683 |      401.65 |      5.9956 |





#### Loss/Perplexity vs Epochs
![Alt text](logs.png)


# Part 2 - Quora Duplicate Pair

## Loading Data

The file `quora_duplicate_questions.tsv` was used.

## Parsing Files
The `pd.read_csv` method was used (with ` sep="\t"`) to read the files. We are only interested in using the questions marked as duplicate (i.e. `is_duplicate ==1`)

Only the question1 and question2 columns were retained.

There were no missing values 


## String Reversal

Reversing the input string (as done in the class) improved the results - loss was slighlty less than without reversing string

## Metric
The Accuracy metric cannot be used. Instead, perplexity - which is the exponent of the loss value - is recorded.


## Results



#### Training Log
|    epoch    |   Train PPL |  Train Loss |   Valid PPL |  Valid Loss |
| ----------- | ----------- | ----------- | ----------- | ----------- | 
|           1 |      168.34 |       5.126 |      129.11 |      4.8607 |
|           2 |      68.464 |      4.2263 |      84.001 |      4.4308 |
|           3 |      43.166 |       3.765 |      68.202 |      4.2225 |
|           4 |      32.583 |      3.4838 |      59.996 |      4.0943 |
|           5 |      26.535 |      3.2785 |      55.842 |      4.0225 |
|           6 |      22.678 |      3.1214 |      52.708 |      3.9648 |
|           7 |      19.708 |       2.981 |      50.279 |      3.9176 |
|           8 |      18.061 |      2.8938 |      50.096 |      3.9139 |
|           9 |      16.287 |      2.7904 |      47.811 |      3.8673 |
|          10 |      14.984 |       2.707 |      47.831 |      3.8677 |
|          11 |       13.83 |      2.6268 |      47.765 |      3.8663 |
|          12 |      12.781 |       2.548 |      46.946 |       3.849 |
|          13 |      11.972 |      2.4826 |      46.952 |      3.8491 |
|          14 |      11.736 |      2.4626 |       44.65 |      3.7989 |
|          15 |      10.937 |      2.3922 |      46.191 |      3.8328 |
|          16 |      10.314 |      2.3335 |      46.604 |      3.8417 |
|          17 |      10.011 |      2.3037 |      46.233 |      3.8337 |
|          18 |      9.4836 |      2.2496 |      48.637 |      3.8844 |
|          19 |      9.2145 |      2.2208 |      45.993 |      3.8285 |
|          20 |      8.6916 |      2.1624 |      48.593 |      3.8835 |



#### Loss/Perplexity vs Epochs
![Alt text](logs2.png)



# Part 3 - English-German Translation (using Multi30k)
I wanted to translate from English to TUrkish. Unfortunately, spacy doesn't support Turkish, so I had to go with German. :) 

## Loading Data

Since the Multi30k dataset is part of the legacy code (and might be deprecated), I downloaded the original files from github using wget


## Parsing Files
The `pd.read_csv` method was used (with ` sep="\t"`) to read the files. 


## Metric
The Accuracy metric cannot be used. Instead, perplexity - which is the exponent of the loss value - is recorded.

## Model
The same model that was presented in the class has been used to train and evaluate (including teacher-forcing for the former)

## Results



#### Training Log
|    epoch    |   Train PPL |  Train Loss |   Valid PPL |  Valid Loss |
| ----------- | ----------- | ----------- | ----------- | ----------- | 
|           1  |      20.194  |      3.0054  |      17.243  |      2.8474  |
 |           2  |      12.579  |       2.532  |      14.515  |      2.6752  |
 |           3  |      10.336  |      2.3356  |      13.238  |      2.5831  |
 |           4  |      8.6194  |       2.154  |      12.732  |      2.5441  |
 |           5  |      7.5958  |      2.0276  |      11.899  |      2.4765  |
 |           6  |      6.6891  |      1.9005  |      11.787  |       2.467  |
 |           7  |      6.0315  |       1.797  |      11.185  |      2.4146  |
 |           8  |      5.4878  |      1.7025  |      11.416  |       2.435  |
 |           9  |      5.0367  |      1.6167  |      11.442  |      2.4373  |
 |          10  |      4.6311  |      1.5328  |      11.426  |      2.4359  |
 |          11  |      4.3749  |      1.4759  |      11.332  |      2.4276  |
 |          12  |      4.0922  |      1.4091  |      11.794  |      2.4676  |
 |          13  |       3.869  |       1.353  |       12.21  |      2.5022  |
 |          14  |      3.6742  |      1.3013  |      12.088  |      2.4922  |
 |          15  |      3.5334  |      1.2623  |      12.359  |      2.5143  |
 |          16  |      3.3694  |      1.2147  |      12.429  |      2.5201  |
 |          17  |      3.2581  |      1.1812  |      12.436  |      2.5206  |
 |          18  |      3.1669  |      1.1528  |      12.548  |      2.5295  |
 |          19  |      3.0316  |      1.1091  |      13.289  |      2.5869  |
 |          20  |      2.9951  |       1.097  |       13.33  |      2.5901  |





#### Loss/Perplexity vs Epochs
![Alt text](logs3.png)

#### Samples
![Alt text](samples3.png)


# Part 4- Chatbot Design (using Multi30k)
I wanted to design a chatbot. The official pytorch tutorial suggested using the [Cornell Movie--Dialogs Corpus](https://www.cs.cornell.edu/~cristian/Cornell_Movie-Dialogs_Corpus.html)  

## Loading Data

Data files were downloaded from http://www.cs.cornell.edu/~cristian/data/cornell_movie_dialogs_corpus.zip. One of the files had the dialogs along with their ids. ANother file mapped ids to a sequence indicating pair(s) of dialog. 

## Metric
The Accuracy metric cannot be used. Instead, perplexity - which is the exponent of the loss value - is recorded.

## Model
The same model that was presented in the class has been used to train and evaluate (including teacher-forcing for the former)


## Training Log
![Alt text](logs4.png)

## Samples
![Alt text](samples4.png)

## Discussion
For the chatbot, the results were not good! Infact, we need a much better model!
