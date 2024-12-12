
# How to Extract and Interact? Nested Siamese Text Matching with Interaction and Extraction
![image](https://github.com/hggzjx/nie_match/assets/103107137/69e18fff-3d03-474f-b3c3-96c9de389c6d)

For citation, please refer to:
> Zang, J., Liu, H. (2023). How to Extract and Interact? Nested Siamese Text Matching with Interaction and Extraction. In: Iliadis, L., Papaleonidas, A., Angelov, P., Jayne, C. (eds) Artificial Neural Networks and Machine Learning – ICANN 2023. ICANN 2023. Lecture Notes in Computer Science, vol 14258. Springer, Cham. https://doi.org/10.1007/978-3-031-44192-9_42

## NIE-Match Model

<img width="3111" alt="Figure2" src="https://github.com/hggzjx/nie_match/assets/103107137/6a6a3037-1746-436e-ac9f-aa6397375235"><br>

Overview of NIE-Match. (a) Model Structure; (b) Encoder; (c) Function Amplification Module (FAM), comprising two options; (d) Interaction Extraction Module (IFM), comprising two options.
How to run the model in the project

#tensorflow >= 1.14<br>
#keras >= 2.3.1<br>
python train.py

## Training with your own data

Process your own dataset into a csv file with three fields for header sentence1, sentence2, label, as shown below:

<img width="136" alt="image" src="https://user-images.githubusercontent.com/103107137/228113859-4f78b407-718e-46c7-9308-4e47c6a385dc.png"><br>

Split the data into train.csv, dev.csv, test.csv and put them in . /datasets/dataset folder.

Here are some commonly used text matching and natural language inference datasets:

1. SNLI (Stanford Natural Language Inference): This dataset is a widely-used natural language inference dataset provided by Stanford University. It contains around 50,000 labeled pairs of text, including three labels: entailment, contradiction, and neutral.
Download Link: https://nlp.stanford.edu/projects/snli/
2. QQP (Quora Question Pairs): This dataset is created by Quora and consists of pairs of questions from the Quora website. The task is to determine if two questions are semantically similar or not.
Download Link: https://www.kaggle.com/c/quora-question-pairs/data
3. MRPC (Microsoft Research Paraphrase Corpus): This dataset is created by Microsoft Research and consists of sentence pairs that are labeled as either paraphrases or non-paraphrases. The sentences were extracted from news articles, and the dataset is commonly used for evaluating text matching and paraphrasing models.
Download Link: https://www.microsoft.com/en-us/download/details.aspx?id=52398
4. STS (Semantic Textual Similarity) Dataset: This dataset is a collection of sentence pairs that are labeled with a similarity score indicating the degree of semantic similarity between the two sentences. The dataset includes both news articles and tweets, and it is often used for evaluating text matching and semantic similarity models.
Download Link: https://ixa2.si.ehu.es/stswiki/index.php/Main_Page
5. SICK (Sentences Involving Compositional Knowledge) Dataset: This dataset is a collection of sentence pairs that are labeled as either entailment, contradiction, or neutral. The sentences were designed to test compositional knowledge, which refers to the ability to combine words and phrases to create new meanings. The dataset includes both simple and complex sentence structures, and it is commonly used for evaluating natural language inference models.
Download Link: http://clic.cimec.unitn.it/composes/sick.html
6. MNLI (Multi-Genre Natural Language Inference): This dataset is also provided by Stanford University and includes over 400,000 labeled pairs of text. It includes a wider range of text genres than SNLI and also has three labels: entailment, contradiction, and neutral.
Download Link: https://cims.nyu.edu/~sbowman/multinli/
7. GLUE (General Language Understanding Evaluation): This is a collection of nine natural language understanding tasks that can be used to evaluate language models. The tasks include sentence classification, text matching, and paraphrasing.
Download Link: https://gluebenchmark.com/
8. RTE (Recognizing Textual Entailment): This dataset is a collection of pairs of text created for the purpose of evaluating natural language inference systems. The task is to determine if a piece of text entails another piece of text.<br>
Download Link: https://aclweb.org/aclwiki/Recognizing_Textual_Entailment_(RTE)_Datasets

## Hyperparameter Setting

Set the parameters of the corresponding model in the corresponding position in the train.py script. The Implementation Details are shown as below：

The experiments are conducted using the BiLSTM and BERT as the encoders of the MIE-Match model framework respectively. The MIE-Match model has different hyperparameter settings on different datasets, and some common hyperparameters are listed here as follows. The parameters of the pre-trained BERT are Layer = 24, Hidden = 1024, Head = 16, the size of the BiLSTM encoder is 64, the size of the BiLSTM used in the model subject is 128, and the size of the hidden layer of the fully connected layer MLP in the main body of the MIE-Match is 64. Cross-entropy is used as the loss function in the experiments, using $\beta_1 = 0.9$ and The Adam optimizer with $\beta_2 = 0.999$ is trained for 30 epochs, and the optimal model is selected using the early stop mechanism. 
