# TFSE
Implementation of the paper "Molecular Designing of Potential Environmentally Friendly PFAS Based on Deep Learning and Generative Models" by Ying Yang, Zeguo Yang, Xudi Pang, Huiming Cao*, Yuzhen Sun, Ling Wang, Zhen Zhou, Pu Wang, Yong Liang* and Yawei Wang\*
---
This code is based on the following works：  
  - [DGL-LifeSci: An Open-Source Toolkit for Deep Learning on Graphs in Life Science](https://pubs.acs.org/doi/10.1021/acsomega.1c04017)
  * [D-MPNN: Analyzing Learned Molecular Representations for Property Prediction](https://pubs.acs.org/doi/full/10.1021/acs.jcim.9b00237)
  - Cao's work [Screening of the Antagonistic Activity of Potential Bisphenol A Alternatives toward the Androgen Receptor Using Machine Learning and Molecular Dynamics Simulation](https://pubs.acs.org/doi/full/10.1021/acs.est.3c09779)
  - Zhou's work [Describe Molecules by a Heterogeneous Graph Neural Network with Transformer-like Attention for Supervised Property Predictions](https://pubs.acs.org/doi/full/10.1021/acsomega.1c06389)
### Install dependencies　　
    We have provided relevant installation script examples, please refer to them and make changes according to your environment.
#### DGL-lifesci
For the complete code package list, please refer to the [DGL-lifesci.yaml](./DGL-lifesci.yaml)
#### DMPNN
For the complete code package list, please refer to the [chemprop.yaml](./chemprop.yaml)
#### MolHGT and MolHGT+
For the complete code package list, please refer to the [MolHGT+.yaml](./MolHGT+.yaml)

### Instruction
#### ML：This includes all the source code of ML-based models in this study.
#### GNNs：This includes all the source code of AFP,GAT,GCN in this study.
#### DMPNN：This includes all the source code of DMPNN in this study.
* **Running script examples**：
 ```
# D-MPNN
chemprop_hyperopt --dataset_type regression --num_iters 50 --data_path SurFace1414_seed1_train.csv --separate_val_path SurFace1414_seed1_val.csv --separate_test_path SurFace1414_seed1_test.csv --config_save_path Config/config_SurFace1414_seed1.json
chemprop_train --data_path SurFace1414_seed1_train.csv --separate_val_path SurFace1414_seed1_val.csv --separate_test_path SurFace1414_seed1_test.csv --dataset_type regression --save_dir checkpoints/SurFace1414_seed1 --config_path Config/config_SurFace1414_seed1.json --metric r2 --epochs 300 --extra_metrics rmse mae --gpu 0
 ``` 
#### MolHGT：This includes all the source code of MolHGT in this study.
* **Running script examples**：
 ```
# MolHGT
python main_model_hpOpt.py --model molHgt --dirIn data/molnet/DILI5293_c --dirOut ws/DILI5293 --extFeat 0 --datas seed1 --evals 20 --gpu 1
 ``` 
#### MolHGT+:To improve the predictive capability of the MolHGT framework, an advanced MolHGT+ framework was produced that incorporates RDkit molecular descriptors as additional feature inputs.　　
* **Running script examples**：
 ```
# MolHGT+
python main_model_hpOpt.py --model molHgt --dirIn data/molnet/DILI5293_c --dirOut ws/DILI5293 --extFeat 1 --datas seed1 --evals 20 --gpu 1
 ```
### Generative Models:This includes the four molecular generation methods in this study.The ChemTSv2 model, which is based on recurrent neural networks (RNNs), the ORGAN model, which uses generative adversarial networks (GANs), the variable autoencoders (VAE) model, and the GMtransformer model, which is based on transformers.　
