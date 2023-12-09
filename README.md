# USC BA estimator
We provide Python code to estimate brain age (BA) from a raw T1-weighted MRI scan (brain.mgz file). Users will first need to create the brain.mgz file using FreeSurfer software, which is freely available at https://surfer.nmr.mgh.harvard.edu/. Our architecture takes as input a T1-weighted MRI scan and processes it as described in the original publication. 
Sample code to calculate BA in a sample subject is provided in "/function/3D_CNN.ipynb". Our weight file, which contain the compressed model architecture, are in the "/function/model" folder. We suggest using Google Colab or Jupyter notebook to execute our code. This software is valid for estimating the brain ages of persons whose chronological age is over 21. For persons under age 21, estimated brain ages may not be accurate. Direct all questions and comments to irimia@usc.edu.  Please acknowledge the original publication when using this code:

Yin, Chenzhong, et al. "Anatomically interpretable deep learning of brain age captures domain-specific cognitive impairment." Proceedings of the National Academy of Sciences 120.2 (2023): e2214634120.

# Install modules and packages required by 3D-CNN model
Click the **Applications** folder in your dock, then **Utilities**, then **Terminal**. 
Type the command after the dollar sign and hit enter:
```
$ pip install -r requirements.txt
```

# Get files ready to run the model
Run FreeSurfer: https://github.com/tannerjared/MRI_Guide/wiki/FreeSurfer-7-Suggested-Processing #The first step is suffcient for this because all you need is a brain.mgz file as input

Copy your files into a USC Brain Age input directory. Here's an example if they all have the same prefix and are named consecutively. You will need to change paths and prefix and more but this is just an example to make a directory for each participant in a set location and then copy the brain.mgz file from each participant's FreeSurfer processed directory.
```
for i in {1..10}; do
current_value="sub-$(printf "%03d" "$i")";
mkdir ~/neurotools/USC_BA_estimator/input/${current_value} ;
cp ~/neurotools/fs_subjects/${current_value}/mri/brain.mgz ~/neurotools/USC_BA_estimator/input/${current_value}/brain.mgz ;
done
```
# Run the .ipynb notebook
I ran the notebook on a Windows 11 computer running Ubuntu in WSL2. Python and all the needed packages (see requirements) were already installed. Then I opened the .ipynb notebook (clone the repository and change directories in the function fdirectory) using the WSL2 version of Visual Studio Code, edited the paths to fit where the USC_BA_estimator and all data were, and then ran the notebook. Make sure you select an appropriate Python interpreter.
