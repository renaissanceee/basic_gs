# 3D Gaussian Splatting for Real-Time Radiance Field Rendering
Bernhard Kerbl*, Georgios Kopanas*, Thomas Leimkühler, George Drettakis (* indicates equal contribution)<br>

## Installation
```shell
git clone https://github.com/renaissanceee/basic_gs.git
cd basic_gs

conda create -y -n basic_gs python=3.8
conda activate basic_gs

pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 -f https://download.pytorch.org/whl/torch_stable.html
conda install cudatoolkit-dev=11.3 -c conda-forge

pip install -r requirements.txt

pip install submodules/diff-gaussian-rasterization
pip install submodules/simple-knn
```
## Run
```shell
python train.py -s {dataset_dir}/{scene} -m {output_dir}/{scene} --eval --white_background

python render.py -m benchmark_ficus_x8 --skip_train -r 1 --suffix {}
python metrics.py -m benchmark_ficus_x8 -r 1 --suffix {}
```