STRUCTURED ILLUMINATION MICROSCOPY (SIM) RECONSTRUCTION PIPELINE
===============================================================

OVERVIEW

Python implementation for SIM image reconstruction with:

GPU-accelerated version (CuPy)

CPU version (NumPy)

Processes raw TIFF stacks organized by angle/phase, performs Wiener deconvolution, and outputs high-resolution reconstructions.

DATA REQUIREMENTS

File naming convention:
Angle_[XX]Phase[YYY].tiff (e.g., Angle_45_Phase_0.071.tiff)

Folder structure:
/sim_data/
Angle_45_Phase_0.071.tiff
Angle_45_Phase_0.143.tiff
Angle_45_Phase_0.214.tiff
Angle_90_Phase_0.071.tiff
...

9 files required per reconstruction (3 angles × 3 phases)

Supported angles: 45°, 90°, 135° (modifiable in code)

KEY FEATURES

Input Processing:

Automatic angle/phase extraction from filenames

TIFF stack loading and cropping

Reconstruction:

Wiener filtering

Fourier domain processing

Frequency order extraction

Output:

High-resolution TIFF

Reference image

Visualization tools

INSTALLATION

GPU Version (Recommended):
pip install cupy scikit-image matplotlib tifffile

CPU Version:
pip install numpy scipy scikit-image matplotlib tifffile

USAGE

Place TIFF files in folder

Update path in script:
folder_path = "/path/to/sim_data"

Run:
GPU: python sim_reconstruction_gpu.py
CPU: python sim_reconstruction_cpu.py

OUTPUT FILES

Raw_cropped_reference.tiff

SIM_output_halfsize.tiff

PERFORMANCE TUNING

Adjustable parameters:
alpha = 0.1 # Wiener filter noise control [0.01-0.5]
k_exc_rel = 0.42 # Excitation frequency [0.3-0.5]
crop_factor = 1 # 1=full size, 2=50% crop

NOTES

Only processes .tif/.tiff files with "Angle" in name

Phase values must be decimal format (e.g., 0.071)

Modify angle_list/phase_list for non-standard patterns

PIPELINE STEPS

Raw TIFF loading

Filename parsing

Image cropping

Wiener deconvolution

Fourier processing

Order extraction

Image reconstruction

Output generation

AUTHOR

Dr. Hassan Dibaji
Postdoctoral Researcher - Optical Imaging Systems
