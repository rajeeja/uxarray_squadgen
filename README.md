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

Or, if running from a Python notebook, set the PATH in Python:
```python
import os
os.environ["PATH"] = "/Users/mbook/SQuadGen:" + os.environ["PATH"]
```
export PATH="$PATH:/Users/mbook/SQuadGen"
```

### 3. Generate a Regionally Refined Mesh (from anywhere)
Example command (adjust region as needed):
```sh
SQuadGen --grid_type CS --refine_type LOWCONN --refine_level 2 --resolution 10 --output output_mesh.nc --refine_rect "-110.0,35.0,-105.0,40.0,2"
```
This creates `output_mesh.nc` in your working directory.

### 3. Install Python dependencies
```sh
conda activate uxarray_env3.12
pip install uxarray jupyter matplotlib
```

### 4. Run the notebook
Open `uxarray_squadgen_full_demo.ipynb` in Jupyter Notebook or JupyterLab. The notebook will:
- Set up your PATH for SQuadGen in Python
- Generate a regionally refined mesh (from scratch, using SQuadGen)
- Visualize the mesh with uxarray and matplotlib
- Explain all SQuadGen command line options used

## Example SQuadGen Command
```
SQuadGen --grid_type CS --refine_type LOWCONN --refine_level 2 --resolution 10 --output output_mesh.nc --refine_rect "-110.0,35.0,-105.0,40.0,2"
```
- `--grid_type CS`: Use a Cubed Sphere grid. Other options: ICO (Icosahedral), OCT1, OCT2.
- `--refine_type LOWCONN`: Use the LOWCONN refinement scheme. Other options: CUBIT, LOWCONNOLD.
- `--refine_level 2`: Number of refinement levels to apply. Higher means more local refinement.
- `--resolution 10`: Base mesh resolution (number of cells along one edge of a panel).
- `--output output_mesh.nc`: Output filename for the generated mesh (NetCDF format).
- `--refine_rect "-110.0,35.0,-105.0,40.0,2"`: Define a rectangular region to refine.
  - Format: `lon_min,lat_min,lon_max,lat_max,refine_level`
  - Here: longitudes -110 to -105, latitudes 35 to 40, refinement level 2.

You can adjust these parameters to focus refinement on other regions or increase mesh density.

## Demo Workflow

The recommended workflow is to use the Jupyter notebook `uxarray_squadgen_full_demo.ipynb`.

- **Generates a regionally refined mesh from scratch using SQuadGen** (no .nc file needed)
- **Visualizes the mesh with uxarray and matplotlib**
- **Explains all SQuadGen command line options and workflow steps**
- **Sets up the PATH for SQuadGen automatically in Python**

To run the demo:

1. Make sure you have Python 3.8+ and the required packages installed:
   - `uxarray`, `jupyter`, `matplotlib`
   - You can install them via pip or conda, e.g.:
     ```sh
     pip install uxarray jupyter matplotlib
     # or
     conda install uxarray jupyter matplotlib
     ```
2. Launch Jupyter:
   ```sh
   jupyter notebook uxarray_squadgen_full_demo.ipynb
   ```
3. **IMPORTANT:**
   - Edit the notebook to set the correct path to your SQuadGen executable (default is `/Users/mbook/SQuadGen`).
   - If you use a different Python environment or install location, update the notebook and commands accordingly.

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.
