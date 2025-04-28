# Gazing at Rewards: Eye Movements as a Lens into Human and AI Decision-Making in Hybrid Visual Foraging

Authors: Bo Wang, Dingwei Tan, Yen-Ling Kuo, Zhaowei Sun, Jeremy M. Wolfe, Tat-Jen Cham, Mengmi Zhang

This repository contains the official implementation of our CVPR 2025 paper:

**"Gazing at Rewards: Eye Movements as a Lens into Human and AI Decision-Making in Hybrid Visual Foraging"**

[![Paper](https://img.shields.io/badge/Paper-Arxiv-red?logo=arxiv)](https://arxiv.org/pdf/2411.09176)
[![Poater](https://img.shields.io/badge/Paper-Poster-brightgreen)](https://drive.google.com/file/d/1nRiaT9_IlPOOIN-m2OhXiruvoomdWRhA/view?usp=sharing)

## Project Description
Imagine searching a collection of coins for quarters ($0.25$), dimes ($0.10$), nickels ($0.05$), and pennies ($0.01$)—a hybrid foraging task where observers look for multiple instances of multiple target types. In such tasks, how do target values and their prevalence influence foraging and eye movement behaviors (e.g., should you prioritize rare quarters or common nickels)? To explore this, we conducted human psychophysics experiments, revealing that humans are proficient reward foragers. Their eye fixations are drawn to regions with higher average rewards, fixation durations are longer on more valuable targets, and their cumulative rewards exceed chance, approaching the upper bound of optimal foragers. To probe these decision-making processes of humans, we developed a transformer-based Visual Forager (VF) model trained via reinforcement learning. Our VF model takes a series of targets, their corresponding values, and the search image as inputs, processes the images using foveated vision, and produces a sequence of eye movements along with decisions on whether to collect each fixated item. Our model outperforms all baselines, achieves cumulative rewards comparable to those of humans, and approximates human foraging behavior in eye movements and foraging biases within time-limited environments. Furthermore, stress tests on out-of-distribution tasks with novel targets, unseen values, and varying set sizes demonstrate the VF model’s effective generalization. Our work offers valuable insights into the relationship between eye movements and decision-making, with our model serving as a powerful tool for further exploration of this connection.

<p align="center">
  <img src="Fig1a.png" alt="Fig1a" width="54%">
  <img src="Fig1b.png" alt="Fig1b" width="37%">
</p>

An example of scanpath is shown below:

<table style="width: 100%; text-align: center;">
  <tr>
    <td><img src="target_combination.png" width="200"></td>
    <td><img src="human_fixations.gif" width="200"></td>
    <td><img src="model_fixations.gif" width="200"></td>
  </tr>
  <tr>
    <td>Target combination</td>
    <td>Human fixations</td>
    <td>Model fixations</td>
  </tr>
</table>

## Installation

conda create -f environment.yml

## Download

We acknowledge Brady, et al. for using their stimulus: http://olivalab.mit.edu/MM/uniqueObjects.html.

If you want to use the exactly the same stimulus we choose, please download them from https://drive.google.com/drive/folders/1OoaAXTsjB_PIhKMw3SuBBG4POq2ReCro?usp=share_link and put them into [env1](./first-training-stage/visual_foraging_gym/envs/) and [env2](./second-training-stage/visual_foraging_gym/envs/)

Download pretrained model from https://drive.google.com/drive/folders/1JMXkr1bNewBRpggOIRc8nfRi0grh76OB?usp=share_link and replace the folder [data](./second-training-stage/data/).

For human data downloading, see the instruction in [README](./human-foraging-data-analysis/README.md).

## Usage
To train the model:
1. Run the first training stage
```
cd first-training-stage
python train.py
```

2. Run the second training stage
```
cd second-training-stage
./runSecondStageTrain.sh
```

To test the model:
```
cd second-training-stage
./test_full_vf.sh
```

## Results
After testing the model, use [npy2csv](./human-foraging-data-analysis/npy2csv.ipynb) to convert .npy results to .csv files.

To plot Norm.Score: run matlab code [plot_cumulativeScore.m](./human-foraging-data-analysis/plot_cumulativeScore.m).

<img src="Norm_Score.png" width="600">

To plot saccade size: run matlab code [plot_saccade.m](./human-foraging-data-analysis/plot_saccade.m).

<img src="saccadeSize.jpg" width="300">

To plot Spider of OOD performance: run matlab code [plot_spyder.m](./human-foraging-data-analysis/plot_spyder.m).

<img src="oodSpyder.jpg" width="300">

To plot Click Bias Ratio: run matlab code [plot_ClickBiasRatio.m](./human-foraging-data-analysis\plot_ClickBiasRatio.m)

<img src="ClickBiasRatio.jpg" width="300">

## Citation

If you use this code, please cite our paper:
```
@article{wang2024gazing,
  title={Gazing at Rewards: Eye Movements as a Lens into Human and AI Decision-Making in Hybrid Visual Foraging},
  author={Wang, Bo and Tan, Dingwei and Kuo, Yen-Ling and Sun, Zhaowei and Wolfe, Jeremy M and Cham, Tat-Jen and Zhang, Mengmi},
  journal={arXiv preprint arXiv:2411.09176},
  year={2024}
}
```
