# 3D Gaussian Splatting for Real-Time Radiance Field Rendering
Bernhard Kerbl*, Georgios Kopanas*, Thomas Leimkühler, George Drettakis (* indicates equal contribution)<br>

## Installation
```shell
git clone https://github.com/renaissanceee/3DGS_base.git
cd 3DGS_base

conda create -y -n 3DGS_base python=3.8
conda activate 3DGS_base

pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 -f https://download.pytorch.org/whl/torch_stable.html
conda install cudatoolkit-dev=11.3 -c conda-forge

pip install -r requirements.txt

pip install submodules/diff-gaussian-rasterization
pip install submodules/simple-knn
```
## Run
```shell
python train.py -s {dataset_dir}/{scene} -m {output_dir}/{scene} --eval --white_background
```