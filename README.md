This repository is a replication package associated with the paper entitled: **FlakyCat: Predicting Flaky Tests Categories using Few-Shot Learning**.
We provide all the code and data used for our experiments, that could be easily replicated with the given notebooks.

# FlakyCat
FlakyCat is an approach for classifying the causes of flakiness, relying on the pre-trained model codebERT and Few Shot Learning based on Siamese networks. 

## Dataset 

The data folder contains the following  : 
1.  ***data/test_files_v0*** : contains the original data collected for this study, 451 flaky tests categorized according to their causes of flakiness. The file names have the following format : `ProjectName.ClassName.TestName@Category`

2.  ***data/test_files_v12*** : contains data obtained after an augmentation of the original data. the file `data_augmentation.zip` provides the code used for this augmentation.

3. ***data/vectors***:  contains the data vectors created by codeBERT. 

4. ***data/Dataset_informations.xlsx*** : provides dataset construction details. 

5. ***data/Statements_analysis.xlsx*** : Analysis performed to answer RQ3 of the associated paper. 



## Replicating experiments


### Requirements 
- Python
- Trax ( not compatible with windows ) 
- Transformers
- scikit_learn
- [TestSmellDetector.jar](https://github.com/TestSmells/TestSmellDetector/releases)


### Notebooks 

The code used is provided in notebooks form : 

#### CodeBERT based experiments 

The notebook `codeBERT-based` shows the classification experiments conducted using the source code transformation performed by the codeEBRT model. This notebook includes the main experiment of Flakycat,  and compares it to the baseline methods. The folder `model` contains the saved trained model. 

#### Test-Smells based : 

In the notebook `smells-based`, we perform experiments based on the vectors produced by the [TsDetect](https://testsmells.org/pages/testsmelldetector.html) Tool. 
We use the following command to detect test smells in each test : 

  > java -jar .\TestSmellDetector.jar pathToInputFile.csv
  
 The input csv file should have the following format:

  > PorjectName,pathToTestFile,pathToProductionFile

The tool outputs a CSV file containing the results of the execution `data/vectors/results_ts_detect.csv`

#### Vocabulary based 

contains the code for experiments based on the flakiness vocabulary.

