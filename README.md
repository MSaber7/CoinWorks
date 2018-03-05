
<img src="https://user-images.githubusercontent.com/6023331/36913973-4c09184c-1e11-11e8-83a2-18dfc6b1b938.png" width="72" height="72"/> &nbsp;&nbsp;&nbsp;&nbsp;
<img src="https://user-images.githubusercontent.com/6023331/36926816-47501caa-1e3f-11e8-8fa8-bee5cdff3dfe.png" width="72" height="72"/>


# CoinWorks

<h3>3. [Under submission] ChainNet: Learning on Blockchain Graphs with Topological Features</h3>
  <p>Using persistent homology based ideas, we offer an elegant, easily extendable and computationally light approach for graph representation learning on Blockchain networks to predict cryptocurrency prices.</p>

 <h3>2. <a href = "http://cakcora.github.io/blockchain/576.pdf">Forecasting Bitcoin Price with Graph Chainlets </a> (PAKDD 2018) </h3>
  <p>We introduce a novel concept of chainlets, or Bitcoin subgraphs, which allows us to evaluate the local topological structure of the Bitcoin graph over time.</p>

  <h3>1. <a href = "http://cakcora.github.io/blockchain/blockchainsurvey1_1.pdf">Blockchain: A Graph Primer</a></h3>
  <p>Aug 2017 Version 1.1</p>
  <p>We offer a holistic view on Blockchain. Starting with a brief history, we give the building blocks of Blockchain,
and explain their interactions. As graph mining has become a major part its analysis, we elaborate on graph theoretical
aspects of the Blockchain technology.</p>


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See the prerequisites that you need to deploy this project to your environment.

### Prerequisites

What things you need to install the software and how to install them

```
Python 3.5
Tensorflow r1.1
```

### Installing

Please visit the given links to install required software to run CoinWork project.

```
Python Installation     : https://www.python.org/downloads/
Tensorflow Installation : https://www.tensorflow.org/install/
```

Anaconda is recommended to be used for installation of both python and tensorflow. Anaconda is a open source distribution of Python and it simplifies package management and deployment. Please visit https://anaconda.org/ for more information.

## Authors
 - Nazmiye Ceren ABAY
 - Cuneyt Gurcan AKCORA

## Project Structure
Here, our project is divided into two main parts as data files and source codes written in Java and Python.

### Data Files
Our data spans from 2009 to 2018 in each file:
<ul>
  <li> <a href="/data/dailyOccmatrices2009-2018.rar">Chainlet occurrence matrices (1MB)</a>: Each data file contains the matrix of the day. The file occ2009003.csv gives a 20x20 matrix of chainlet occcurences for year 2009 and day 003.</li>
  <li><a href="/data/dailyAmoMatrices2009-2018.rar">Chainlet amount matrices: (3.8MB)</a>: Each data file contains the matrix of the day. The file amo2009003.csv gives a 20x20 matrix of chainlet amounts for year 2009 and day 003.</li>
  <li> <a href="/data/feature.txt">Graeve's feature values(3.8MB)</a>: Extracted daily features</li>
  <li> Betti numbers <a href="/data/betti_0(100).csv">0</a> and <a href="/data/betti_1(100).csv">1</a> </li>
  <li> <a href="/data/filteredDailyOccMatrices.rar">Filtered occurence matrices</a></li>
  <li> <a href="/data/pricedBitcoin2009-2018.csv">Bitcoin prices</a></li>
</ul>

### Source Files


 * [src](./src)
    * [main](./src/main)
        * [python](./python)
            * [bitcoin_prediction](./bitcoin_prediction)
                * [bitcoin_tests](./bitcoin_tests)
                    * In this folder, we put bitcoin test files to predict log return of bitcoin with recursive neural network (RNN) and random forest algorithms.
                * [sliding](./sliding)
                    * [slided_regression.py](./sliding/slided_regression.py)
                        * This class can be used to predict bitcoin both for betti numbers and chainlets. It takes 3 file parameters to run prediction model bitcoin price file, chainlet file and result file.
                    * [filtration_regression.py](./sliding/filtration_regression.py)
                        * For given threshold values, chainlets are filtrated and fed into the prediction model. For each threshold, one model is constructed and output its prediction.
                    * [boosting_of_filtrated_regression.py](./sliding/boosting_of_filtrated_regression.py)
                        * This class takes the previously constructed models of filtration_regression.py and re-build the stronger deep learning model with them.
## Deep Learning Network Structure
In this project, for both slided and filtration techniques, regression of deep learning is used for constructing the model for prediction of Bitcoin system. While constructing deep learning, we have used 4 hidden layer with hyperbolic tangent activation function. To get better convergence of gradient descent, Xavier weight initialization technique is applied. For avoiding the overfitting of training bitcoin sets, dropout technique is used as a regularization technique and its value is 0.2 for each hidden layer.
