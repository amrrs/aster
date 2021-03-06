# aster - a bot to write kaggle baseline kernels
Aster is a python based bot (or a module), which is capabale of writing baseline starter kernels for competitions or datasets hosted on Kaggle. As of now, It can work with two types of datasets - numerical dataset (having continuous and / or categorical columns) and text datasets having single text / document field. 

### Key features 

1. Can create kernels on Compeititon and Datasets both  
2. Can create kernels on datasets with binary / multi classification  
3. Can create kernels on text datasets and numerical datasets  
4. Performs Quick Exploration, Preprocessing, Feature Engineering, and Modelling  
5. Changes the visuals according to data, for example - generates word clouds for text data and pairplots for numerical datasets
6. Uses a config to create new kernels  

### How Aster Works  

Aster first understands the inputs given in the config by the user and the types of columns present in the dataset.  According to this information, aster dynamically chooses the most relevant code / text templates and appends them to the baseline kernel. For example, if the dataset is belongs to text classification category, then aster will generate some wordclouds, will not perform correlation charts, pair plots or categorical variable distributions. While if the dataset is non text classification type, then aster will choose the most relevant templates, for example - distribution of categorical variables, missing value treatments etc.  

### Detailed table of contents  

Aster creates following contents based on the type of data.

1. Environment Preparation
2. Quick Exploration   
&nbsp;&nbsp;&nbsp;&nbsp; 2.1 Load Dataset    
&nbsp;&nbsp;&nbsp;&nbsp; 2.2 Dataset Snapshot and Summary    
&nbsp;&nbsp;&nbsp;&nbsp; 2.3 Target Variable Distribution    
&nbsp;&nbsp;&nbsp;&nbsp; 2.4 Missing Values    
&nbsp;&nbsp;&nbsp;&nbsp; 2.5 Variable Types  
&nbsp;&nbsp;&nbsp;&nbsp; 2.6 Variable Correlations
3. Preprocessing  
&nbsp;&nbsp;&nbsp;&nbsp; 3.1 Label Encoding    
&nbsp;&nbsp;&nbsp;&nbsp; 3.2 Missing Values Treatment     
&nbsp;&nbsp;&nbsp;&nbsp; 3.3 Feature Engineering (text fields)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.3.1 TF-IDF Vectorizor  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 3.3.2 Top Keywords - Wordcloud    
&nbsp;&nbsp;&nbsp;&nbsp; 3.4 Train Test Split    
4. Modelling   
&nbsp;&nbsp;&nbsp;&nbsp; 4.1 Logistic Regression  
&nbsp;&nbsp;&nbsp;&nbsp; 4.2 Decision Tree    
&nbsp;&nbsp;&nbsp;&nbsp; 4.3 Random Forest  
&nbsp;&nbsp;&nbsp;&nbsp; 4.4 ExtraTrees Classifier  
&nbsp;&nbsp;&nbsp;&nbsp; 4.5 Extereme Gradient Boosting  
5. Feature Importance   
6. Model Ensembling  
&nbsp;&nbsp;&nbsp;&nbsp; 6.1 A simple Blender  
7. Creating Submission

### Useage : example 1

```python
from aster.aster import aster

config = {	"COMPETITION" : "titanic", 
            "_TARGET_COL" : "Survived", 
            "_ID_COL" : "PassengerId"}

ast = aster(config) # aster object with config 
ast._prepare() # prepare the kernel
ast._push() # push the kernel on kaggle
```

### Useage : example 2

```python
from aster.aster import aster

config = {	"COMPETITION" : "spooky-author-identification", 
            "_TARGET_COL" : "author", 
            "_ID_COL" : "id",
            "_TAG" : "doc",
            "_TEXT_COL" : "text"}

ast = aster(config) # aster object with config 
ast._prepare() # prepare the kernel
ast._push() # push the kernel on kaggle
```

### config examples 

Aster uses config and its key-value pairs to write kernels on different datasets. All of the keys are not mandatory and most of them are optional. Check the following table.  

Key | Example Value | Default | Optional/Mandatory | Definition
--- | --- | --- | --- | ---
DATASET | iris | "" | optional | Name of the dataset to be used 
COMPETITION | titanic | "" | optional | Name of the competition 
_TARGET_COL | Survived | "" | mandatory | target column name
_ID_COL | PassengerId | "" | optional | id column name 
_TRAIN_FILE | train | train | optional | name of the train file
_TEST_FILE | test | test | optional | name of the test file 
_TAG | doc | num | optional (only for text) | doc : text dataset, num : numerical dataset
_TEXT_COL | text | "" | optional (only for text) | name of the column containing text data

### Example Kernels generated by Aster 

###### 1. Binary Classification on Numerical Data - Competition Data
- Titanic Baseline Kernel :   

###### 2. Multi Classification on Text Data - Competition Data
- Spooky Author Baseline Kernel   


###### 3. Classification - Non Competition Data   
- Iris Dataset   


- Diabetes Dataset   


- Mushrooms Dataset    


### Installation

Aster can be installed directly from github using following commands 

```shell
git clone https://github.com/shivam5992/aster.git
cd textstat
python setup.py install
```

### Future Work

- Dynamic Code Selection Improvements       
- Add More Content     
&nbsp;&nbsp;&nbsp;&nbsp;- Automated Feature Engineering     
&nbsp;&nbsp;&nbsp;&nbsp;- Hyperparameter Tuning     
- Extend Datatypes     
&nbsp;&nbsp;&nbsp;&nbsp;- Regression Problems - Numerical Data     
&nbsp;&nbsp;&nbsp;&nbsp;- Image Classifiication          
