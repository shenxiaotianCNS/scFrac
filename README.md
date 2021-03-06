# scFrac
Using a SVR method to deconvolute the cell fraction in a mixture sample using single cell seq data
![image](https://user-images.githubusercontent.com/69139997/140094678-e12e4e6e-2287-4cbb-acad-7b3582a5c077.png)

# install:
devtools::install_github(“shenxiaotianCNS/scFrac”)

# usage:
	scfrac(mixture,seuratobjext,nPerm)

# example using built in data:

#### YY is the mixture matrix, with sample in colum and gene in row
	scFrac::YY[1:10,1:10]
     	TCGA-DD-A4NG-01A TCGA-G3-AAV4-01A TCGA-2Y-A9H1-01A TCGA-BC-A10Y-01A TCGA-K7-AAU7-01A TCGA-BC-A10W-01A TCGA-DD-AACV-01A TCGA-DD-AAD3-01A TCGA-DD-A39X-11A
	Saa3      0.000000000       0.00000000        0.0000000       0.00000000      0.193145155       0.06098851       0.00000000      0.000000000      0.000000000
	Slpi      0.000000000       0.01298560        0.0000000       0.00000000      0.007151308       0.00000000       0.00000000      0.000000000      0.000000000
	Cfd       0.992363695       1.47831339        2.0442644       0.95705156      1.869666411       0.86207485       2.84978438      1.686785001      1.044961450
	Gsn       0.000000000       0.00000000        0.0000000       0.00000000      0.000000000       0.00000000       0.00000000      0.000000000      0.000000000
	Mgp       1.392656043       0.92825171        0.4713262       0.71804958      1.459199734       1.98783478       1.09027908      1.561597709      0.233239536
	C3        2.817509427       2.55078471        1.2341101       2.57167794      4.036040339       3.62839474       2.52398312      2.178161108      1.467522500
	Clu       0.000000000       0.00000000        0.0000000       0.00000000      0.000000000       0.00000000       0.00000000      0.000000000      0.000000000
	Apoe      0.007685404       0.00000000        0.0000000       0.01545603      0.045854259       0.02200552       0.04186160      0.003619704      0.001381904
	Spp1      6.314781981       6.89906641        7.6036875       6.42415254      6.695148838       6.33296179       6.46912497      6.382021747      5.771885926
	Gpx3      0.000000000       0.04264948        0.1331687       0.24864715      0.136112062       0.18798788       0.09950746      0.227252876      0.000000000
	     TCGA-DD-A1EI-01A
	Saa3      0.640680779
	Slpi      0.000000000
	Cfd       1.794992695
	Gsn       0.000000000
	Mgp       1.586118993
	C3        3.427686108
	Clu       0.000000000
	Apoe      0.004095529
	Spp1      6.936311336
	Gpx3      0.287640770

#### Fibroblast_ is a seurat object
	scFrac::fibroblasts_
	An object of class Seurat 
	13851 features across 200 samples within 1 assay 
	Active assay: RNA (13851 features, 2000 variable features)
	 2 dimensional reductions calculated: pca, umap
 
 
##### running: using nPerm=5
	scfrac(fibroblasts_[,1:200],YY[,1:20],nPerm = 5)
	Calculating cluster iCAF
	  |++++++++++++++++++++++++++++++++++++++++++++++++++| 100% elapsed=01s  
	Calculating cluster myCAF
	  |++++++++++++++++++++++++++++++++++++++++++++++++++| 100% elapsed=01s  
	Calculating cluster apCAF
	  |++++++++++++++++++++++++++++++++++++++++++++++++++| 100% elapsed=01s  
	[1] 1
	[1] 2
	[1] 3
	[1] 4
	[1] 5
	                      myCAF      iCAF        apCAF
	TCGA-DD-A4NG-01A 0.09992375 0.8937604 0.0063158924
	TCGA-G3-AAV4-01A 0.09720270 0.8974404 0.0053569342
	TCGA-2Y-A9H1-01A 0.08198760 0.9149265 0.0030859354
	TCGA-BC-A10Y-01A 0.09793974 0.8926296 0.0094306161
	TCGA-K7-AAU7-01A 0.10658258 0.8874751 0.0059422883
	
# release
## 0.1.0 
only SVR was added,
the elastic network regression and xgboost regression will be added soon 
