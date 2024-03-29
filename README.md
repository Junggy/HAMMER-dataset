# On the Importance of Accurate Geometry Data for Dense 3D Vision Tasks (HAMMER-dataset)
Official dataset for [On the Importance of Accurate Geometry Data for Dense 3D Vision Tasks](https://arxiv.org/abs/2303.14840) (**HAMMER** : **H**ighly **A**ccurate **M**ulti-**M**odal Dataset for **DE**nse 3D Scene **R**egression)

**direct link to download the full dataset**: http://www.campar.in.tum.de/public_datasets/2022_arxiv_jung/_dataset_processed.zip

## Scenes
HAMMER dataset comprises 13 scenes (scene**XX**) that are splitted into 10 scenes for training (scene2-11) and 3 scenes (scene12-14) for testing. Each scene has two trajectories (sceneXX_**trajX**) that are divided into few continous sequences (sceneXX_trajX_**X**) and extra trajectories that covers exactly same viewpoint but without any objects that is suitable for object removal task (sceneXX_trajX_**naked**_X)

## Sensor Modalities
Our dataset is acquired with custom rig that comprises depth sensor for **I-ToF (Lucid Helios)**, **Active Stereo (Intel Realsense D435)**, **D-ToF (Intel Realsense L515)** and RGB sensor for **Polarization camera (Lucid Pheonix camera with Sony polarization sensor)**.
we included rendered depth for each depth sensors (d435, l515, tof)such that one can evaluate each modality with absolute ground truth. For RGB sensor (polarization), we forwardly warped each depth sensor's depth into RGB such that one can train the network with different modalities as well as absolute ground truth.

## Monocular Depth Estimation
We trained monocular depth estimation with two different setups. First use MonoDepth2 (https://github.com/nianticlabs/monodepth2) architecture with without supervision to show negative impact of noisy sensor depth when it is used as ground truth which eventually performs worse on the challenging material compared to self-supervised training (Metric : RMSE in mm).

### Experiment on MonoDepth2

|         Training Signal         | Full Scene | Background | All Objects |  Diffused | Reflective | Transparent |
|:-------------------------------:|:----------:|:----------:|:-----------:|:---------:|:----------:|:-----------:|
|              I-ToF              |   113.29   |   111.13   |    119.72   |   54.45   |    87.84   |    207.89   |
|              D-ToF              |    77.97   |  **69.87** |    112.83   | **37.88** |    71.59   |    207.85   |
|          Active Stereo          |  **72.20** |    71.94   |  **61.13**  |   50.90   |    52.43   |    87.24    |
|  Self Supervised (with GT pose) |   154.87   |   158.67   |    65.42    |   57.22   |  **37.78** |  **61.86**  |
| Self Supervised (Mono + Stereo) |   159.80   |   161.65   |    82.16    |   71.24   |    63.92   |    66.48    |

Due to strong artifacts of ToF sensor on the challenging materials (Reflective & Transparent) Active Stereo scores higher on evaluation on Full Scene & Objects compared to other depth modality even with qualitatively worse result.
For the challenging materials (Reflective & Transparent), self supervision score better result compared to using depth sensor as supervision signal.



## Novel View Synthesis from Implicit 3D Reconstruction
Evaluation against GT for RGB, depth and surface normal estimates for different optimisation strategies (+ denotes sensor depth in modality column). We use vanila NeRF [1] (https://github.com/bmild/nerf) for RGB only training and Dense Depth Prior NeRF [2] (https://github.com/barbararoessle/dense_depth_priors_nerf) to train NeRF with sensor depth. We indicate best with **bold text**, depth metrics in mm.

| Modality | (RGB) PSNR | (RGB) SSIM | (Depth) AbsRel | (Depth) SqRel | (Depth) RMSE | (Depth) e<1.25 | (Normal) Cos.Sim |
|:--------:|:----------:|:----------:|:--------------:|:-------------:|:------------:|:--------------:|:----------------:|
|    RGB [1]  | **32.406** |    0.889   |      0.328     |    111.229    |    226.187   |      0.631     |       0.084      |
| + AS    [2]     |   17.570   |    0.656   |      0.113     |     0.113     |    16.050    |      0.853     |       0.071      |
| + iToF [2]  |   18.042   |    0.653   |      0.296     |     0.296     |    91.426    |      0.520     |       0.102      |
| + dToF [2]  |   31.812   |    0.888   |      0.112     |     0.112     |    24.988    |      0.882     |       0.031      |
| + GT    [2]    |   32.082   |  **0.894** |    **0.001**   |   **0.001**   |   **0.049**  |    **1.000**   |     **0.001**    |

For more details, please check our paper : https://arxiv.org/abs/2303.14840
