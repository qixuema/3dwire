# 3D HOUSE WIREFRAME DATASET

## Description

This project is dedicated to working with 3d house wireframe datasets stored in NPZ files. It includes a Python script for reading and visualizing 3D wireframe data using the Open3D library. The dataset and related scripts are organized to facilitate easy loading, processing, and visualization of 3D wireframes.

For more details, please visit our project homepage: [https://vcc.tech/research/2024/3DWire](https://vcc.tech/research/2024/3DWire).

## Dataset Download

You can download the 3D house wireframe dataset from the following link:
[Download Dataset](https://drive.google.com/drive/folders/1omp0mBoR8Z4jdHGM4V3699qO59fHfGhm?usp=sharing)

Once downloaded, extract the zip file into the `npz` directory as shown in the directory structure below.

## Directory Structure

```
3D_HOUSE_WIREFRAME_DATASET/
│
├── npz/
│   ├── 00000.npz
│   ├── 00001.npz
│   ├── ...
│   └── [more NPZ files]
│
├── read_npz.py
│
└── README.md
```

- **npz/**: This directory contains the NPZ files with the 3D house wireframe data.
- **read_npz.py**: A Python script for reading and visualizing the wireframe data from NPZ files.
- **README.md**: This file, providing an overview of the project.


## Installation
The code is tested in docker enviroment [nvidia/cuda:12.4.1-cudnn-devel-ubuntu22.04](https://hub.docker.com/layers/nvidia/cuda/12.4.1-cudnn-devel-ubuntu22.04/images/sha256-0a1cb6e7bd047a1067efe14efdf0276352d5ca643dfd77963dab1a4f05a003a4).
The following are instructions for setting up the environment in a Linux system from scratch.

First, clone this repository:

    git clone https://github.com/qixuema/3dwire.git
    # or (with SSH)
    git clone git@github.com:qixuema/3dwire.git

Then, make sure you have [UV](https://github.com/astral-sh/uv) installed.  
If not, install it with:

      pip install uv

Next, create the environment and install dependencies:

      cd 3dwire
      uv sync

Finally, activate the environment:

      source .venv/bin/activate   # On Linux

To train the model, please use the following commands:

      # Train vqvae
      accelerate launch --config_file configs/default_config.yaml train_vqvae.py --config configs/train_vqvae.yaml

      # Train transformer
      accelerate launch --config_file configs/default_config.yaml train_transformer.py --config configs/train_transformer.yaml

## DATA Visualization

### Prerequisites

Make sure you have Python installed along with the necessary libraries:
- `open3d`
- `numpy`

You can install these libraries using pip:
```bash
pip install open3d numpy
```

### Running the Script

To visualize a 3d house wireframe from an NPZ file, follow these steps:

1. Update the `file_path` variable in `read_npz.py` to point to the desired NPZ file.
2. Run the script:
   ```bash
   python read_npz.py
   ```

### Script Explanation

The `read_npz.py` script performs the following tasks:
1. Loads the vertices and lines data from the specified NPZ file.
2. Checks if the data is correctly loaded.
3. Creates a `LineSet` object using Open3D.
4. Visualizes the wireframe using Open3D's visualization tools.


## Acknowledgments

- Thanks to the [Open3D](https://www.open3d.org/) and [NumPy](https://numpy.org/) communities for providing the essential tools for this project.
- We appreciate the [RPLAN](http://staff.ustc.edu.cn/~fuxm/projects/DeepLayout/index.html) for providing the fundamental floor plans of House.
- Thank you to [Sepid Hosseini](https://github.com/sepidsh) for providing the code for extracting vertices and edges of the House floor plan.
- We are grateful for the [scikit-geometry](https://github.com/scikit-geometry/scikit-geometry) Python library for providing the tools to extract roof straight skeletons.
- We appreciate [vector-quantize-pytorch](https://github.com/lucidrains/vector-quantize-pytorch) for offering essential tools that played a key role in our network model development.
- We thank [x-transformers](https://github.com/lucidrains/x-transformers) for providing a flexible and powerful transformer implementation that supported our project.

## Citation
If you find our work useful in your research, please consider citing:

	@InProceedings{3DWire24,
	  title={Generating 3D House Wireframes with Semantics}, 
	  author={Xueqi Ma and Yilin Liu and Wenjun Zhou and Ruowei Wang and Hui Huang},
	  booktitle={ECCV},
	  pages={223-240},
	  year={2024}
	}
