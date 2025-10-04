# environment-setup
files for setting up development environments

This repo contains a setup for setting up dev environments for machine learning and working with python based on my personal setup for projects. The first setup is based on using conda as the environment manager and was my main manager while at KTH. I am now migrating to a uv setup not only for a fast installation process and management but also in support of oss and science after this [happened](https://www.theregister.com/2024/08/08/anaconda_puts_the_squeeze_on/). 

I still keep the conda setup going because there are many cases when I need it but I really despise working with requirements.txt files which is another reason for working with uv. 

## Conda 
1. Install conda 
2. **Create environment** - conda env create -f workbench.yaml 
3. **Activate environment** - conda activate workbench 
4. **Update packages** - conda updatge --all 
5. **Clean up packages** - conda clean --all 
6. **Uninstall environment** - conda remove --name workbench --all 

## UV 