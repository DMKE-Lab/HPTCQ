# HPTCQ

HPTCQ: Hierarchical Pattern-based of Temporal Knowledge Graph Complex Query

This repository contains the implementation of the HPTCQ architectures described in the paper.

## Installation
* Python 3.x(tested on Python 3.6)
* Pytorch 1.2.0
* SPARQLWrapper
* torch
* datasets
* numpy
```bash
pip install python 3.6
pip install pytorch
pip install SPARQLWrapper
pip install torch
pip install datasets
pip install numpy

```
## Train and Test

### 1. Preprocess data for HPTCQ
```bash
cd ./preprocess
sh run_me.sh
```

### 2. Training for HPTCQ

execute the following command for training.
```bash
sh train.sh
```

### 3. Testing for HPTCQ
Modify the following content in `./eval.sh`.
```bash
devices=$1
save_name=$2
dbpedia_endpoint=$3
```
* Replace `$1` with the id of the GPU to be used.  
* Replace `$2` with the path of the trained model.  
* Replace `$3` with the address of the established DBpedia SPARQL service

Then, execute the following command
```bash
sh eval.sh
```

### 4. Generate candidate queries
Modify the following content in `./generate_queries.sh`.
```bash
test_data=$1          
dbpedia_endpoint=$2   
```
then, execute the following command

```bash
sh generate_queries.sh
```
The candidate queries for the training set, valid set, and test set are saved under `./data` directory.


### 5. Preprocess data for query ranking model
```bash
cd ./model_ranking
sh run_me.sh
```

### 6. Training for query ranking model
Modify the following content in `./model_ranking/train.sh`.
```bash
devices=$1
```
* Replace `$1` with the id of the GPU to be used.
Then, execute the following command for training query ranking model.
```bash
cd ./model_ranking
sh train.sh
```
The trained query ranking model file is saved under `./model_ranking/runs` directory. 

#### 7. Test for query ranking model
Modify the following content in `./query_ranking/eval.sh`.
```bash
devices=$1
save_name=$2
dbpedia_endpoint=$3
```
* Replace `$1` with the id of the GPU to be used.  
* Replace `$2` with the path of the trained model.  
* Replace `$3` with the address of the established DBpedia SPARQL service

Then, execute the following command for the final results of query.
```bash
cd ./model_ranking
sh eval.sh
```
