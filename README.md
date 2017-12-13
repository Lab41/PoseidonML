# Poseidon: Machine Learning - Phase II

## Overview
This repository contains the components necessary to build a docker container that can be used for training a number of ML models using network packet captures (pcaps).  The repository includes scripts necessary to do the training (e.g. "train_OneLayerModel.py") as well as doing the evaluation once a model has been trained (e.g. "eval_OneLayer.py")  

While this repository and resulting docker container can be used completely independently, this code was written to support the Cyber Reboot Vent and Poseidon projects. See:

[Vent](https://github.com/CyberReboot/vent) plugins for evaluating
machine learning models on network data as part of the
[Poseidon](https://github.com/CyberReboot/poseidon) SDN project.

## Plugins
The current supported plugins are:

### NodeClassifier
Plugin for traffic classification to determine device types and their behavior.

### Rough Getting Started
1. Get the bits: git clone https://github.com/Lab41/PoseidonML.git
2. Build the docker container:
    a. "cd PoseidonML/NodeClassifier/"
    b. "./build-docker.sh"
3. Collect your training pcaps and put them into a directory (tcpdump is what we usually use)
4. Launch the docker container: "docker run -it -v /home/<user>/PoseidonML:/app poseidonml bash"
5. create config file called “label_assignments.json” in pcaps dir

6. To train a model: python train_OneLayerModel.py <pcapdir> <filename>.picklefile
7. Once trained, to evaluate using that model: python eval_OneLayer.py <pcapdir> <filename>.picklefile

Output is currently JSON to STDOUT
