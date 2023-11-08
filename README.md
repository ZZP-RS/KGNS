## Introduction
KGLR is a new recommendation framework for long tail recommendations. KGLR is based on the graph neural network framework, which expands the long tail interest of users and enhances the long tail item representation using co-occurrence graphs to provide high-quality recommendations.

## Author
Zhipeng Zhang 

{School of Computer Science and Artificial Intelligence, Liaoning Normal University, Dalian, China}

## Environment Requirement
The code has been tested running under Python 3.7.10. The required packages are as follows:
* torch == 1.8.0
* numpy == 1.23.5
* pandas == 1.5.3
* scipy == 1.10.1
* tqdm == 4.65.0
* scikit-learn == 1.2.2

## KRALR operation steps
1. run selector.py to generate Long-tail Neighbors
~~~
python selector.py
~~~
2. run doCooccur.py to construct Co-occurrence graph and merge Co-occurrence graph and KG
~~~
python doCooccur.py
~~~
3. start KGLR
~~~
python main_KGLR.py
~~~

## datasets
We provided two datasets to validate KGLR: last-fm and ml-1m, the former obtained from KGAT, and the latter is a version released by Movielens-1m. The following table shows the information of two datasets:

|                | Last-FM |  ml-1m  |
| :------------: | :-----: | :-----: |
|    n_users     |  23566  |  6040   |
|    n_items     |  48123  |  3655   |
| n_interactions | 3034796 | 997579  |
|   n_entities   | 106389  | 398505  |
|  n_relations   |    9    |   57    |
|   n_triples    | 464567  | 3396595 |

The pretraining embedding we provide comes from KGAT