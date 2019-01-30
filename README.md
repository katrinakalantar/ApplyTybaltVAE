# ApplyTybaltVAE
Modified scripts to apply the Greene Lab Tybalt VAE to Host and Microbe mNGS data

The original .ipynb files were forked from here: https://github.com/greenelab/tybalt

This directory contains the modified files used specifially for applying the Tybalt model to the combined host and microbial mNGS data.

Scripts were run in the following order...

1. Step1_concatenate_data.ipynb
2. Step2_process_data.ipynb
3. Step3_tybalt_vae.ipynb
4. Step4_tse_tybalt_features.ipynb
5. Step5_extract_tybalt_weights.ipynb


**Step1_concatenate_data.ipynb**
This file reads in the raw gene count data to generate a matrix of genes x samples. It then reads in the raw microbe data and calculates the phylogenetic counts at the genus, family, and category levels. The two matrices are merged to generate a combined host and microbe count table.


**Step2_process_data.ipynb**
The combined host and microbe data frame is read in and preprocessed prior to running Tybalt. In particular, samples with low gene counts are removed and the 5000 most variable features (genes and taxonomic IDs) are selected. These features are then zero-one scaled.


**Step3_tybalt_vae.ipynb**
The matrix of variable features per sample is used to test the Tybalt VAE. This script contains all the parameters originally included with the Tybalt model. Training and test sets are separated and model loss is computed at each epoch of training. Some summary plots are used to show the performance of the final trained model.


**Step4_tse_tybalt_features.ipynb**
To evaluate the information captured by the VAE reduced dimensionality representation, TSNE is run for both the full dataset and the reduced dimensionality dataset. Additional clustermaps have been added to visualize the encodings for each latent dimension across all the samples.


**Step5_extract_tybalt_weights.ipynb**
This script identifies genes that are significantly associated with each latent dimension. The weights for each latent dimension are plotted on the TSNE representation.




