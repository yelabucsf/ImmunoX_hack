# ImmunoX hackathon 2019
Instructions for setting up environment for scRNA-seq analysis using `scanpy` for Python or `seurat` for R.  
You don't need both packages, choose whatever you are familiar with.  
 
# Python *scanpy* setup for MacOS and Windows   
Use the following link:  
https://www.anaconda.com/distribution/#download-section  

Select your operating system and click download for **Python 3.7 version**  
Open downloaded file and follow the instructions.  

### MacOS setup  
1. Open terminal.  
2. `conda create -n immunox_hack19 pip`  
3. `source activate immunox_hack19` - this will activate your environment where you will install packages and perform analysis.  
4. `conda install pandas numpy scipy`  
5. Next set of commands will install `scanpy` and dependencies   
```shell script
conda install seaborn scikit-learn statsmodels numba pytables
conda install -c conda-forge python-igraph louvain
pip install leidenalg
pip install scanpy python-igraph louvain
```
**NOTE:** Advanced users feel free to set up your environment as you please.

6. In your Anaconda Navigator select created environment and click install button under Jupyter Lab icon.  

### Windows setup  
1. Anaconda Prompt.  
2. `conda create -n immunox_hack19 pip`  
3. `source activate immunox_hack19` - this will activate your environment where you will install packages and perform analysis.  
4. `conda install pandas numpy scipy`  
5. Next set of commands will install `scanpy` and dependencies   
```shell script
conda install seaborn scikit-learn statsmodels numba pytables seaborn
conda install -c conda-forge python-igraph louvain
pip install leidenalg
pip install scanpy python-igraph louvain
```
**NOTE:** Advanced users feel free to set up your environment as you please.

6. In your Anaconda Navigator select created environment and click install button under Jupyter Lab icon.  



# R *seurat* setup for MacOS and Windows  
Use the following link:  
https://www.rstudio.com/products/rstudio/download/

Select *RStudio Desktop* and click download
Open downloaded file and follow the instructions.  

### MacOS and Windows setup  
1. Open Rstudio.  
2. `install.packages('Seurat')`


# Tutorial links:  
### PBMC clustering with scanpy  
https://scanpy-tutorials.readthedocs.io/en/latest/visualizing-marker-genes.html

### Cell clustering with Seurat
https://satijalab.org/seurat/vignettes.html


# Importing your datasets  
This will help you to import your datasets for gene and surgace protein expression  

### scanpy  
```python
import scanpy as sc
adata = sc.read_10x_h5("FULL_PATH_TO_FILE", gex_only=False)
```


### seurat  
```R
library(Matrix)
matrix_dir = "/opt/sample345/outs/filtered_feature_bc_matrix/"
barcode.path <- paste0(matrix_dir, "barcodes.tsv.gz")
features.path <- paste0(matrix_dir, "features.tsv.gz")
matrix.path <- paste0(matrix_dir, "matrix.mtx.gz")
mat <- readMM(file = matrix.path)
feature.names = read.delim(features.path, 
                           header = FALSE,
                           stringsAsFactors = FALSE)
barcode.names = read.delim(barcode.path, 
                           header = FALSE,
                           stringsAsFactors = FALSE)
colnames(mat) = barcode.names$V1
rownames(mat) = feature.names$V1
```