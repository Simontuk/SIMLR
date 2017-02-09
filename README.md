**SIMLR** *(Single-cell Interpretation via Multi-kernel LeaRning)*
===============================


**OVERVIEW**

Single-cell RNA-seq technologies enable high throughput gene expression measurement of individual cells, and allow the discovery of heterogeneity within cell populations.  Measurement of cell-to-cell gene expression similarity is critical to identification, visualization and analysis of cell populations. However, single-cell data introduce challenges to conventional measures of gene expression similarity because of the high level of noise, outliers and dropouts. We develop a novel similarity-learning framework, *SIMLR* (Single-cell Interpretation via Multi-kernel LeaRning), which learns an appropriate distance metric from the data for dimension reduction, clustering and visualization. *SIMLR* is capable of separating known subpopulations more accurately in single-cell data sets than do existing dimension reduction methods. Additionally, *SIMLR* demonstrates high sensitivity and accuracy on high-throughput peripheral blood mononuclear cells (PBMC) data sets generated by the GemCode single-cell technology from 10x Genomics. 

**SIMLR**

*SIMLR* offers three main unique advantages over previous methods: (1) it learns a distance metric that best fits the structure of the data via combining multiple kernels. This is important because the diverse statistical characteristics due to large noise and dropout effect of single-cell data produced today do not easily fit specific statistical assumptions made by standard dimension reduction algorithms. The adoption of multiple kernel representations provides a better fit to the true underlying statistical distribution of the specific input scRNA-seq data set; (2) *SIMLR* addresses the challenge of high levels of dropout events that can significantly weaken cell-to-cell similarities even under an appropriate distance metric, by employing graph diffusion, which improves weak similarity measures that are likely to result from noise or dropout events; (3) in contrast to some previous analyses that pre-select gene subsets of known function, *SIMLR* is unsupervised, thus allowing de novo discovery from the data. We empirically demonstrate that *SIMLR* produces more reliable clusters than commonly used linear methods, such as principal component analysis (PCA), and nonlinear methods, such as t-distributed stochastic neighbor embedding (t-SNE), and we use *SIMLR* to provide 2-D and 3-D visualizations that assist with the interpretation of single-cell data derived from several diverse technologies and biological samples. 

Furthermore, here we also provide an implementation of *SIMLR* (see SIMLR large scale) capable of handling large scale datasets. 

**REFERENCE**

The latest draft of thr manuscript related to *SIMLR* can be found as a preprint at http://biorxiv.org/content/early/2016/06/09/052225. 

**DOWNLOAD**

We provide both the R and MATLAB implementations of *SIMLR* (both standard and large scale) in the SIMLR branch, while the master (stable version) or the development (development version) branches provide the version of *SIMLR* available on Bioconductor. 

Furthermore, we also provide a Python implementation for SIMLR which can be found at https://github.com/bowang87/SIMLR_PY. 

**RUNNING SIMLR R IMPLEMENTATION**

We provide the R code to run *SIMLR* on 4 examples in the script *R_main_demo.R*. Furthermore, we provide a large scale implementation of *SIMLR* (see large scale implementation) with 1 example in the script *R_main_demo_large_scale.R*. The R libraries required to run the 2 demos can be installed by running the script *install_R_libraries.R*. We now present a set of requirements to run the examples. 

1) Required R libraries. *SIMLR* requires 2 R packages to run, namely the *Matrix* package (see https://cran.r-project.org/web/packages/Matrix/index.html) to handle sparse matrices and the *parallel* package (see https://stat.ethz.ch/R-manual/R-devel/library/parallel/doc/parallel.pdf) for a parallel implementation of the kernel estimation. 

To run the large scale analysis, it is necessary to install 4 more packages, namely *Rcpp* package (see https://cran.r-project.org/web/packages/Rcpp/index.html), *pracma* package (see https://cran.r-project.org/web/packages/pracma/index.html), *RcppAnnoy* package (see https://cran.rstudio.com/web/packages/RcppAnnoy/index.html) and *RSpectra* package (see https://cran.r-project.org/web/packages/RSpectra/index.html). 

Furthermore, to run the examples, we require the *igraph* package (see http://igraph.org/r/) to compute the normalized mutual informetion metric and the *grDevices* package (see https://stat.ethz.ch/R-manual/R-devel/library/grDevices/html/00Index.html) to color the plots. 

All these packages, can be installed with the R built-in *install.packages* function. 

2) External C code. We make use of an external C program during the computations of *SIMLR*. The code is located in the R directory in the file *projsplx_R.c*. In order to compite the program, one needs to run on the shell the command *R CMD SHLIB -c projsplx_R.c*. 

An OS X pre-compiled file is also provided. Note: if there are issues in compiling the .c file, try to remove the pre-compiled files (i.e., *projsplx_R.o* and *projsplx_R.so*). 

3) Example datasets. The 5 example datasets are provided in the directory data. 

Specifically, the dataset of Test_1_mECS.RData refers to http://www.ncbi.nlm.nih.gov/pubmed/25599176, Test_2_Kolod.RData refers to http://www.ncbi.nlm.nih.gov/pmc/articles/PMC4595712/, Test_3_Pollen.RData refers to http://www.ncbi.nlm.nih.gov/pubmed/25086649 and Test_4_Usoskin.RData refers to http://www.ncbi.nlm.nih.gov/pubmed/25420068. 

Moreover, for the large scale example, the dataset of Zelsel.RData refers to https://www.ncbi.nlm.nih.gov/pubmed/25700174. 

**RUNNING SIMLR MATLAB IMPLEMENTATION**

We also provide the MATLAB code to run *SIMLR* on the 5 examples in the script main_demo.m and main_LARGE_demo_.m. Please refer to the directory *MATLAB* and the file ReadMe.txt within for further details. 
