
# This repository recalls using Hyper3dnet for trees classification using the MAAP  and hyperspectral data

## Description 

At the MAAP stack, the GPU use is enabled.    
This code conduct a supervised training on Hyperspectral data from PRISMA mission using the Hyper3Dnet model. 
The model is implemented with Tensoflow package and it runs using GPU on the MAAP. 

## The workspace 

The Jupyter MAAP stack dev file sample in :  **dev_file_GPU.txt** allows using the GPU. 

	This devfile contains a nodeSelector and a toleratino to be able to use the gpu node.


## datasets and packages 

First thing to do after creating GPU workspace is to dowload data that are stored in the S3. For this task you should : 

*use the S3 script (in windows) : 

    echo $MAAP_ENV_TYPE
	export MAAP_ENV_TYPE=VAL
	export CLIENT_ID=97262f0b-d3ca-4492-bcf8-9a0e12bdede8

* Downloading request using maap-s3.py
	Since data are stored in :  **maap-scientific-data/shared/imane**   
	list first stored files in that repository by runing :
	
		maap-s3.py list /maap-scientific-data/shared/imane/
	
	Download the image file (.mat) : maap-s3.py download maap-scientific-data/shared/imane/*filename* *path_where_to_save_data* 
	
		ex : maap-s3.py download maap-scientific-data/shared/imane/france_region2_data.mat /projects/data/france_region2_data.mat

	Download the ground truth file (.mat) : maap-s3.py download maap-scientific-data/shared/imane/*filename* *path_where_to_save_data*   
	
		ex : maap-s3.py download maap-scientific-data/shared/imane/france_region2_GT.mat /projects/data/france_region2_GT.mat

&nbsp;

*The second step would be installing the required *packages* for the code processing in your working environement weither it's the base env or a vir env
	The required packages are listed in **requirements text file** 
	Please run : 
		
		**pip install -r requirements.txt**
	In your env run : ** conda install -c conda-forge psutil ** 

## Execution 

Followwing the jupyter notebook steps leads to Training the Hyper3Dnet Model with GPU use.
A hint of the cells outputs are in the notebook : **Classiifcation_using_hyper3Dnet.ipynb**

