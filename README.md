# Attention_3DUnetPP_Brain-Tumor-Segementation
this repo contain the implementaiion of paper we are working on wih the team from Jorden Univesity  of science and technology , in this work we present a new based model on Neasted 3DUnet++ combined wiht attention mechanism Block for more effiency feature extracttion 

## the problem case study in 3D Biomedical image processing

- subject
Accurate segmentation of brain tumor sub-regions is essential in the quantifica- tion of lesion burden, providing insight into the functional outcome of patients. In this regard, 3D multi-parametric magnetic resonance imaging (3D mpMRI) is widely used for non-invasive visualization and analysis of brain tumors. Different MRI sequences (such as T1, T1ce, T2, and FLAIR) are often used to provide complementary information about different brain tumor sub-regions

- Problem
in many cases for processing Medical images to get better understanding of disease and impact on human being life such Brain tumor is most area for reseachers to improve system diagnosis in partuclar Task Segementation , last few year lunch of challenge BRATS for segmentation Brain tumor Sub-regrion many of studying came up to improve CAD system ,

- Solution
For automatic segmentation we will use Unet3d To predict the age and number of days of survival: first, we will train the auto-encoder to scale the space from 4 240 240 * 150 to 512, and then extract the statistical values, ​​and hidden representations for each identifier in the data encoded by the pre-trained auto-encoder and based on this tabular data we will train SVR

1. [introduction](#introduction)
2. [environment project](#environment-project)
3. [run project](#run-project)
5. [model]
5. [Results]

### introduction
*Imaging Data Description*

All BraTS multimodal scans are available as NIfTI files (.nii.gz) and describe a) native (T1) and b) post-contrast T1-weighted (T1Gd), c) T2-weighted (T2), and d) T2 Fluid Attenuated Inversion Recovery (T2-FLAIR) volumes, and were acquired with different clinical protocols and various scanners from multiple (n=19) institutions, mentioned as data contributors here.

All the imaging datasets have been segmented manually, by one to four raters, following the same annotation protocol, and their annotations were approved by experienced neuro-radiologists. Annotations comprise the GD-enhancing tumor (ET — label 4), the peritumoral edema (ED — label 2), and the necrotic and non-enhancing tumor core (NCR/NET — label 1), as described both in the BraTS 2012-2013 TMI paper and in the latest BraTS summarizing paper. The provided data are distributed after their pre-processing, i.e., co-registered to the same anatomical template, interpolated to the same resolution (1 mm^3) and skull-stripped.

### environment-project
* setup the enviroment;
	* install script shell 
       here you will need to run script shell to install all the dependencies needed for 
       run code :
       * create [kaggle](https://www.kaggle.com/) account to access to the data API 
       * add path kaggle.json to script shell $path_api
       * create the enviromenet here you will need to run 

                python create_env.py {name of your env}

       * make sure the requirements.txt exist to the repo 
       install the packges if you want fisrt neeed to run 

                pip install -r requirements.txt

       - here you will need to run script shell to install all the dependencies needed automated setup whole project 

                chmod +x automate_downlaod_data.sh && ./automate_downlaod_data.sh
### run-project 

* PostProcessig dataset Brast2020;

    this tool built based on top of BET algorithm that publish from [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/BET) and [N4baisCorrection](https://pubmed.ncbi.nlm.nih.gov/20378467/) we automated the process and handle the data in 3D shape

	* tool description ;

        we develpoed a simple tool that helps to Post Processing the dstaset 
        * N4 bais Correction field this will increase the Low intensity of the image to run :

                   python Postprocessing.py --path {path_name} --n4baiscorrection 

        * Skull Stripping this technic helps to reduce tissues such skull and midbrain .. only we do care about in our project is brain tissues to tun it :

                   python Postprocessing.py --path {path_name} --skull_stripping 

* Virtualization  dataset Brast2020;
     
    to vitualize few samples from the data you need to run this command 
           #the function to plot the corrected with oring img 
            #     type_virtualizer {
            #     option 1 = Anat ,
            #     option 2 = epi ,
            #     option 3 = img ,
            #     
            #  }

            python virtaulizer.py --v2Dreneder plot_type && echo "this will render images in 2D " 

    for rendering the images in 3D you will need to run 

            python virtualizer.py --v3Drender && echo  "this commaned may takes will depmed on the GPU perfomence you have "

