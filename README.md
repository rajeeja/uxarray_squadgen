# uxarray_squadgen

This repository demonstrates how to generate regionally refined meshes using [SQuadGen](https://github.com/MPAS-Dev/SQuadGen) and visualize them with [uxarray](https://github.com/UXARRAY/uxarray).

## Quickstart

### 1. Clone and Build SQuadGen
```sh
git clone https://github.com/MPAS-Dev/SQuadGen.git
cd SQuadGen/src
make
```

### 2. Add SQuadGen to PATH
```sh
export PATH="$PATH:/Users/mbook/SQuadGen"
```

### 3. Generate a Regionally Refined Mesh (from anywhere)
Example command (adjust region as needed):
```sh
SQuadGen --grid_type CS --refine_type LOWCONN --refine_level 2 --resolution 10 --output output_mesh.nc --refine_rect "-110.0,35.0,-105.0,40.0,2"
```
This creates `output_mesh.nc` in your working directory.

### 3. Visualize the Mesh with uxarray
Install dependencies:
```sh
conda activate uxarray_env3.12
pip install uxarray jupyter matplotlib
```

Open the notebook:
```sh
jupyter notebook squadgen_uxarray_demo.ipynb
```

## Files
- `squadgen_uxarray_demo.ipynb`: Example notebook for loading and plotting a mesh.
- `output_mesh.nc`: Example generated mesh (not included in repo).

---

## License
MIT
