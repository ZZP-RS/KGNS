## Introduction
KGNS is a new recommendation framework for long-tail recommendations.

## Environment Requirement
The code has been tested running under Python 3.7.10. The required packages are as follows:
* torch == 1.8.0
* numpy == 1.23.5
* pandas == 1.5.3
* scipy == 1.10.1
* tqdm == 4.65.0
* scikit-learn == 1.2.2

## KGNS operation steps
1. run selector.py to generate Long-tail Neighbors
~~~
python selector.py
~~~
2. run doCooccur.py to construct Co-occurrence graph and merge Co-occurrence graph and KG
~~~
python doCooccur.py
~~~
3. start KGNS
~~~
python main_KGNS.py
~~~

## Ablation study
### Base
1. Replace the training set from longtail_log_.txt to train.txt, and longtail_log_.txt is generated by selector.py, please do not replace data_ Line 22 of the data_loader.py file, which is used to calculate evaluation metrics
2. Replace the knowledge graph file from kg_ Replace kg_final2.txt to kg_final.txt(set on line 24 of the data_loader.py), and kg_final2.txt is generated by doCooccur.py
3. Run code 'python main_KGNS.py' to start Base

### KGNS-UN
1. Replace the knowledge graph file from kg_ Replace kg_final2.txt to kg_final.txt(set on line 24 of the data_loader.py)
2. Run code 'python main_KGNS.py' to start KGNS-UN

### KGNS-IN
1. Replace the training set from longtail_log_.txt to train.txt (set on line 21 of the data_loader.py)
2. Run code 'python main_KRALR.py' to start KGNS-IN


## datasets
We provided three datasets to validate KGNS: MovieLens, LastFM, and Yelp2018. The following table shows the information of three datasets:

|                | LastFM |MovieLens| Yelp2018|
| :------------: | :-----: |  :-----:   | :-----:   |
|    n_users     |  23566  |    6040    |  45919|
|    n_items     |  48123  |    3655    |  45538|
| n_interactions | 3034796 |   997579   | 1185068|
|   n_entities   | 58266  |   398505   | 90961 |
|  n_relations   |    9    |     57     | 42 |
|   n_triples    | 464567  |   3396595  | 1853704 |

Besides the user-item interactions, we need to construct collaborative knowledge graph for each dataset. The following table shows the KG information of LastFM, MovieLens, and Yelp2018

| Knowledge Graph |   Freebase(LastFM)   |  Freebase(MovieLens)  | Freebase(Yelp2018) |
|:---------------:|          :-----------:         |     :-------:     | :-------:     |
|   #entities    |              58266            |       398505      | 90961 |
|   #relations   |                 9              |         57        | 42 |
|    #triples    |              464567            |       3396595     | 1853704 |


