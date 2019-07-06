# MOMF
deconvoluting the bulk RNA-seq data with single-cell RNA-seq data

## Installation
```R
#install devtools packages (devtools package)
install.packages("devtools")
#install MOMF package
devtools::install_github("sqsun/MOMF")
```

## Example
### Simulation data
We have upload the example data (`simData.Rdata`). Data is generated by simulation.<br>
* `GE_list`: list (2), X1: scRNA matrix; X2: bulk RNA matrix. MOMF can also previde the option to deconvolute the single bulk matrix. <br>
* `DataW`: list (2), W1: the initial matrix for scRNA matrix; W2: the initial matrix for bulk RNA matrix.<br>
* `DataH`: matrix, only provide for single bulk deconvulution.<br>
* `celltype`: vector, cell type.<br>
* `priorU`: matrix, reference panel of scRNA matrix.<br>
### Sample code
After install the package and load the simData, you can run the main function `momf.fit` and `momf.computeRef`.
```R
###For two datasets
> load("simData.RData")

# two dataset with reference
> priorU <- ref.compute(GE_list[[1]], celltype)
> momf_res <- momf.fit(DataX = GE_list, DataW = W, DataH=NULL, DataU = U, DataPriorU=t(priorU), method="KL", rho=2, num_iter=3)
# two dataset without reference
> momf_res <- momf.fit(DataX = GE_list, DataW = W, DataH=NULL, DataU = U, DataPriorU=NULL, method="KL", rho=2, num_iter=3)
# proportion of each cell type 
> cell_prop <- momf_res$cell_prop

## Support
Before contacting us, please try the following: <br>
* The methods are described in the papers. <br>

If that doesn't work, you can get in touch with us via the email (sqsun@nwpu.edu.cn,yangsheng@njmu.edu.cn).

### Citation
If you use the software, please cite
