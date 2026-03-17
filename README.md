# CarHoods10k: 3D Point Cloud & Parametric Dataset

![Dataset Size](https://img.shields.io/badge/Dataset-9%2C982_Samples-blue)
![Format](https://img.shields.io/badge/Format-HDF5_%7C_CSV-orange)
![Processing](https://img.shields.io/badge/Compression-400GB+_to_HDF5-red)
![Task](https://img.shields.io/badge/Task-Surrogate_Modeling_%7C_Inverse_Design-success)

## 📌 Overview & My Contribution
**CarHoods10k** is a specialized, large-scale structural engineering dataset designed to bridge the gap between parametric CAD generation, 3D Deep Learning, and true Finite Element Analysis (FEA) physics.

**My Core Contribution:** The [original raw source data](https://datadryad.org/dataset/doi:10.5061/dryad.2fqz612pt) is a massive **400GB+** collection of individual geometry files, FEA outputs, and scattered CSVs. Managing, parsing, and dataloading hundreds of thousands of separate files is a massive bottleneck for training neural networks. 

To solve this, I have **extracted, cleaned, and condensed the entire 400GB+ dataset into a single, high-speed `.h5` (HDF5) file.**  
* 3D geometries were uniformly downsampled to 8,192 points using Area-Based and Farthest Point Sampling (FPS).
* 54 topological CAD parameters were aligned with their respective meshes.
* The result is a highly efficient, plug-and-play dataset ready for immediate PyTorch/TensorFlow ingestion.

## 📊 Dataset Contents

Each sample in the condensed dataset contains:

### 1. Inputs (Geometry & Design)
* **54 CAD Parameters:** Explicit dimensions driving the base sketch and extrusions (e.g., `RibDepth`, `Pocket_Radii`). *Note: Because the dataset contains multiple topological variations (different "skins"), not all 54 parameters are active for every single design.*
* **3D Point Cloud:** 8,192 XYZ coordinates representing the physical 3D surface.

### 2. Targets (FEA Physics)
* **Max Von Mises Stress (MPa):** The maximum localized stress concentration under load.
* **Mass (kg):** Total mass of the resulting car hood.
* **Deformation (mm):** Maximum structural displacement/bending.

