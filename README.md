# HAMMER-dataset

|   Modality  | (RGB) PSNR | (RGB) SSIM | (Depth) AbsRel | (Depth) SqRel | (Depth) RMSE | (Depth) e<1.25 | (Normal) Cos.Sim |
|:-----------:|:----------:|:----------:|:--------------:|:-------------:|:------------:|:--------------:|:----------------:|
| RGB only    | **32.406** |    0.889   |      0.328     |    111.229    |    226.187   |      0.631     |       0.084      |
| RGBD (AS)   |   17.570   |    0.656   |      0.113     |     0.113     |    16.050    |      0.853     |       0.071      |
| RGBD (iToF) |   18.042   |    0.653   |      0.296     |     0.296     |    91.426    |      0.520     |       0.102      |
| RGBD (dToF) |   31.812   |    0.888   |      0.112     |     0.112     |    24.988    |      0.882     |       0.031      |
| RGBD (GT)   |   32.082   |  **0.894** |    **0.001**   |   **0.001**   |   **0.049**  |    **1.000**   |     **0.001**    |

Please check the public dataset website for more details: https://www.campar.in.tum.de/public_datasets/2022_arxiv_jung/

Or use the direct link to download the full dataset: http://www.campar.in.tum.de/public_datasets/2022_arxiv_jung/_dataset_processed.zip
