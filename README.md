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

## Multi-Resol.
```shell
python train.py -s {dataset_dir}/{scene} -m {output_dir}/{scene} --eval --white_background -r 1 --kernel_size 0.1
# general 
python render.py -m benchmark_ficus_ --skip_train -r x --kernel_size 0.1
python metrics.py -m benchmark_ficus_ -r x
# zoom-out
python render.py -m benchmark_ficus_x1 --skip_train -r 8 --suffix kernel --kernel_size 0.1/64 
# zoom-in
python render.py -m benchmark_ficus_x8 --skip_train -r 1 --suffix kernel --kernel_size 0.1*64
python metrics.py -m benchmark_ficus_x8 -r 1 --suffix kernel
```

## Multi-Distance
```shell
# general 
python render.py -m benchmark_ficus_x1_0.1 --skip_train -r 1 -s ../dataset/nerf_synthetic_MS/hotdog/near_z_2 --suffix near_z2 --kernel_size 0.1
python metrics.py -m benchmark_ficus_x1_0.1 -r 1 --suffix near_z2
# zoom-in
python render.py -m benchmark_ficus_x1_0.1 --skip_train -r 1  -s ../dataset/nerf_synthetic_MS/hotdog/near_z_2 --suffix near_z2_0.4 --kernel_size 0.1*4
python metrics.py -m benchmark_ficus_x1_0.1 -r 1 --suffix near_z2 {near_z2_0.4}
```

## Dataset
```shell
wget --no-check-certificate http://storage.googleapis.com/gresearch/refraw360/360_v2.zip
wget --no-check-certificate http://storage.googleapis.com/gresearch/refraw360/360_extra_scenes.zip
```