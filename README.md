# CONTINUED
## CONTINUED: Cluster, integration and annotation of *In situ* metabonomics data
CONTINUED is a algorithm to process *In situ* metabonomics data include reconstruction of histological spatial structure based on single sample clustering, integration of multiple samples and annotation with LC-MS data.
![image](https://github.com/Tang-Lab-super/CONTINUED/assets/120162674/23c75daf-fcee-4c06-b12d-5c547c202419)
![image](https://github.com/Tang-Lab-super/CONTINUED/assets/120162674/0fda6f03-b465-4f76-b8c4-0e2d958c3c68)

### Installation

#### The easy way

Let `devtools` do the installation for you. Type the following in an R shell

```
install.packages("devtools")
devtools::install_github("Tang-Lab-super/CONTINUED",subdir="CONTINUED")
```

#### Manual installation

You can also install it manually as follows:

- Download the latest release [here](https://github.com/3DGenomes/binless/releases/latest)
- Unpack it in a clean folder on your machine, and hit `R CMD INSTALL CONTINUED` in a shell.
- If it complains that some packages are not installed, you must install them in R using `install.packages`

### How does it work?

- In the `example/` folder, we provide datasets and scripts to perform a procession, taken from our data. Alternatively you can use your own data. Start with something not too large, for  example 1Mb. And read on.
- In the `R/` folder, there are three function scripts. `Load.python.functions.py` is mainly applied to `1. Preprocess.R`. It is used for data preprocessing. `Load.r.functions.R` holds all function definitions in R. And `TANG.merge.mass.pl` is the function of multi-sample data processing.
#### Background noise removal
Try out the `1. Preprocess.R`. CONTINUED takes two dataframes contained abundance of m/z as input, in `.txt` format. One is generated under lockmass and another is generated under unlockmass. In order to get the coordinates of the tissue image, CONTINUED also needs a m/z and a corresponding threshold as input. The m/z and threshold were selected according to the shape of the HE staining slice. In function `find_interest_factor`, you will get a dataframe `df_data` and two `.png` files in the `mz_from_path`, the images can help you adjust the parameters. You can get three `.txt` files finally as input for `2. filter.mass.R`.
#### Filter m/z
See `2. filter.mass.R`. It filter m/z max intensity is less than 400.
#### Parameter selection
The clustering results of samples change with the parameter npc and resolution. In `3. parameters.test.R`, you can test a series of npcs and resolutions. Select the final parameters according to the results.
#### Reconstruction of spatial distribution pattern of organization
See `4.1 create_obj.R`. Create three seurat object `.rds` files with parameters selected in `3. parameters.test.R`. You can choose to plot the complete clustering image, the single clustering image or the boundary image. If you have a lot of samples, `4.2 create.obj.with.final.parameters.sh` can help you run more conveniently.
#### Integration and annotation of multiple samples of DESI-MS
We achieve the clustering of m/z by fitting the kernel density function for all m/z values. We also annotate m/zs as specific metabolites. See `5. TANG.merge.mass.pl`. This requires LC-MS databases, either from your own lab, or from an online database. You will get a dataframe containing clustering and annotation information with prefix `colon_cancer_desi`. This is the most important result.
#### Plot kernel density estimation of m/z
See `6. plot.KDE.R`. You can visualize the density distribution of m/z after integration.
#### Plot target m/z
See `7. plot.target.mass.R`. You can visualize the distribution of the same metabolite in different samples.

### More exploration

#### WGCNA and metabolic pathway
If you want to explore the shared metabolic characteristics of the same type of tissue in different samples, try `8.3 run.WGCNA.pathway.R`. To do this, you need to make the input data of the WGCNA using `8.1 share_metabolic.tumor.R`. If you have a lot of samples, `8.2 share_metabolic.tumor.sh` can help you run more conveniently.
#### Plot heatmap of metabolite abundance
See `9. Heatmap.R`. Visualization of the mean abundance of metabolites for each cluster category in each sample.
#### Visualize the spatial relationships of multiple metabolites
See `10. 3D.r`. Here, we create a way to overlap the spatial distribution of multiple metabolites. In this way, you can visualize the spatial relationships of multiple metabolites.

### Questions? Problems?
Check out the [FAQ](https://github.com/Tang-Lab-super/CONTINUED/labels/FAQ) in the GitHub issues tracker. If you don't find anything, just file an issue by clicking on the "New issue" button. You can use it to report bugs, ask questions or suggest new features. We are looking forward to your feedback!



