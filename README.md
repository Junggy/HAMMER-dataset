# On the Importance of Accurate Geometry Data for Dense 3D Vision Tasks (HAMMER-dataset)

## Novel View Synthesis from Implicit 3D Reconstruction
Evaluation against GT for RGB, depth and surface normal estimates for different optimisation strategies (+ denotes sensor depth in modality column). We use Dense Depth Prior NeRF (https://github.com/barbararoessle/dense_depth_priors_nerf) to train NeRF with sensor depth. We indicate best with **bold text**, depth metrics in mm.

| Modality | (RGB) PSNR | (RGB) SSIM | (Depth) AbsRel | (Depth) SqRel | (Depth) RMSE | (Depth) e<1.25 | (Normal) Cos.Sim |
|:--------:|:----------:|:----------:|:--------------:|:-------------:|:------------:|:--------------:|:----------------:|
|    RGB   | **32.406** |    0.889   |      0.328     |    111.229    |    226.187   |      0.631     |       0.084      |
| + AS     |   17.570   |    0.656   |      0.113     |     0.113     |    16.050    |      0.853     |       0.071      |
| + iToF   |   18.042   |    0.653   |      0.296     |     0.296     |    91.426    |      0.520     |       0.102      |
| + dToF   |   31.812   |    0.888   |      0.112     |     0.112     |    24.988    |      0.882     |       0.031      |
| + GT     |   32.082   |  **0.894** |    **0.001**   |   **0.001**   |   **0.049**  |    **1.000**   |     **0.001**    |

Please check the public dataset website for more details: https://www.campar.in.tum.de/public_datasets/2022_arxiv_jung/

Or use the direct link to download the full dataset: http://www.campar.in.tum.de/public_datasets/2022_arxiv_jung/_dataset_processed.zip
