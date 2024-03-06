# Fake News Detection Model - Pradhyumnaa G
This is the entire codebase of the code implemented for CM3070 Final Project.

## Explaining The Folders

### LF0 - Linguistic Feature Set 0 - LF0
Folder containing models trained purely on a word embeddings approach. train_val_test_split.ipynb inside this folder will read the files inside BaseDataset and generate training, validation and testing sets. All other files are models Running them can take anywhere from 30 minutes to 8 hours.

### LF1 - Linguistic Feature Set 1 - LF1
Folder containing models trained using a combination of Word Embeddings and Linguistic Features from Woodworth et al. train_val_test_split.ipynb inside this folder will read the files inside BaseDataset, calculate the linguistic features using the LIWC Dictionary and spaCy model present inside the folder and generate training, validation and testing sets. All other files are models Running them can take anywhere from 1 hour to 10 hours.

### LF2 - Linguistic Feature Set 2 - LF2
Folder containing models trained using a combination of Word Embeddings and Linguistic Features from Gravanis et al. train_val_test_split.ipynb inside this folder will read the files inside BaseDataset, calculate the linguistic features using the LIWC Dictionary and spaCy model present inside the folder and generate training, validation and testing sets. All other files are models Running them can take anywhere from 1 hour to 10 hours.

## Training a Model from Scratch
In order to train a model from scratch, follow these steps.

### 1. Run creating_the_datasets.ipynb
This reads the individual datasets inside Buzzfeed_Politifact, Kaggle, McIntire, Reuters and WELFake and generates two files inside BaseDataset, fake_news.csv and real_news.csv.

### 2. Select either LF0, LF1 or LF2 Folder. Then, run train_val_test_split.ipynb
This is the file that creates training, validation and testing sets. All models in the folder use these files.

### 3.Run a model
These are files that have a model name followed by either main or cv. main is for TFIDF while cv is for Count Vectorizer.

## Running an Existing Model
If you want an example of how to load and run an existing model without following the model training process, follow these steps.

### 1. Select either LF0, LF1 and LF2. Then, go into the Models folder.
Inside these folder, there is a large list of models that have been saved as a result of the model training process within the "Models" folder. Not all models have been exported due to GitHub Repo Size Constraints. Select one of these models. Please note that there is some variation within the LF0 Models folder as some have been trained with a different SVD function and thus, will require some modifications in the next step. 

### 2. Copy a model and place it into the corresponding ModelLoading Folder.
If you wish to run the code without any modification, simply run model_load_file.ipynb.

If you wish to make some modifications, follow these steps. First, select a TFIDF model from the Models Folder and place it into corresponding folden in the ModelLoading Folder. LF0 will contain both model_load_file.ipynb and model_load_text.ipynb while LF1 and LF2 will only have model_load_file.ipynb.

#### Then, modify this line to match the model you have copied.

#Load the SVM Model
model = joblib.load('svm_model_tfidf.joblib')

### 3. Run the File
Run the file and at the end, you will receive an accuracy score of the model evaluated on the unseen test set.

