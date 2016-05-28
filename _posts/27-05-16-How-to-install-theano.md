---
layout: post
title: How to install theano (in ubuntu)
---

# How to install theano in ubuntu

I finally got theano to work in ubuntu. There were quite a few issues with dependencies and incorrectly installed libraries. I am listing down things that worked in the event I require something similar in the future.

1. Create new conda environment with python2. Many have reported problems using theano with python3, and most tutorials and code online seem to be python2 compatible. So, for the time being, lets use python2.
```sh
conda create --name TheanoEnv python=2 pip
```
2. Lets also add some relevent libraries (numpy, scipy etc). Important to pass in the name to make sure that libs are installed only in the environment we want. Idea of creating environment was to simulate a clean slate!
```sh
conda install --name TheanoEnv numpy scipy matplotlib  
```
3. Scipy does not automatically install libs like pillow required for a few image processing tasks. I have to do this manually.
```sh
source activate TheanoEnv
pip install pillow
```
4. Time to install theano
```sh
source activate TheanoEnv
pip install Theano
sudo pip install --upgrade --no-deps theano
```
5. Run tests to make sure that everything is fine.
    - NumPy (~30s):   `python -c "import numpy; numpy.test()"`
    - SciPy (~1m):    `python -c "import scipy; scipy.test()"`
    - Theano (~30m):  `python -c "import theano; theano.test()"`
