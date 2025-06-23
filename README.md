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
python train.py -s {dataset_dir}/{scene} -m {output_dir}/{scene} -r 1 --kernel_size 0.3 --eval --white_background
# zoom-out
python render.py -m benchmark_ficus_x1 --skip_train -r 8 --kernel_size 0.1/64
# zoom-in
python render.py -m benchmark_ficus_x8 --skip_train -r 1 --kernel_size 0.1*64

# baseline
python metrics.py -m benchmark_ficus_x8 -r 1
# new
python metrics.py -m benchmark_ficus_x8 -r 1 --suffix kernel
```