# MOMF
Deconvolution analysis with the bulk RNA-seq data and single-cell RNA-seq data

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
* `GE_list`: list (2), 
      sc_counts: scRNA-seq gene expression matrix (#cells x #genes); 
      bulk_counts: bulk RNA-seq gene expression matrix (#individuals x #genes). <br>

### Toy example
After install the package and load the simData, you can run the main function `momf.fit` and `momf.computeRef`.
```R
### load MOMF package
library(MOMF)

### load example data
> load("toy_example.RData")

# two dataset with reference
> priorU <- momf.computeRef(sc_counts, sc_cell_type)
> GList <- list(X1 = t(sc_counts), X2 = t(bulk_counts))
> momf_res <- momf.fit(DataX = GList, DataPriorU=priorU, method="KL", rho=2, num_iter=3)

# proportion of each cell type 
> cell_prop <- momf_res$cell_prop
```

## Support
If that doesn't work, you can get in touch with us via the email (yangsheng@njmu.edu.cn).

