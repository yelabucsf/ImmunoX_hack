# ImmunoX hackathon 2019
Instructions for setting up environment for scRNA-seq analysis  
 
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