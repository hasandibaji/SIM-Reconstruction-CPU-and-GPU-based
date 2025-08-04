🧠 Structured Illumination Microscopy (SIM) Reconstruction Pipeline

This repository provides Python implementations (both GPU-accelerated using CuPy and CPU-based using NumPy) for loading, preprocessing, and reconstructing high-resolution images using Structured Illumination Microscopy (SIM). It supports raw image stacks organized by angle and phase encoding, and performs Wiener deconvolution to extract and combine frequency orders.

📁 Folder Structure and File Naming Convention

Raw TIFF image files should be organized in a single folder and follow a naming pattern like:

Angle 45 - Phase_0.071.tiff

Angle 45 - Phase_0.143.tiff

Angle 45 - Phase_0.214.tiff

Angle 90 - Phase_0.071.tiff

...

Each SIM angle (e.g., 45°, 90°, 135°) must have three phase-shifted images, for a total of 9 files per reconstruction.

🚀 Features

✅ Loads and crops raw TIFF stacks

✅ Automatically extracts angle and phase info from filenames

✅ Saves the first cropped raw image as reference

✅ Implements SIM reconstruction with:

    Wiener filtering

    Fourier domain shifting

    Frequency order extraction

✅ Outputs final high-resolution image as TIFF

✅ Supports both GPU (cupy) and CPU (numpy) versions

✅ Visualizes raw and reconstructed images

🛠️ Requirements

GPU Version

pip install cupy scikit-image matplotlib

CPU Version

pip install numpy scipy scikit-image matplotlib

🧪 Usage

GPU Version
Update the folder path in the script and run:

python sim_reconstruction_gpu.py

CPU Version

Update the folder path in the script and run:

python sim_reconstruction_cpu.py

🖼️ Output

Raw_cropped_reference.tiff: First cropped input image (used as reference)

SIM_output_halfsize.tiff: Reconstructed high-resolution image

On-screen visualization of both images

📊 Performance Tips

GPU version runs significantly faster on supported NVIDIA hardware.

Center-cropping is currently hard-coded to full size (n=1). You can reduce size to 50% with n=2 in the cropping block.

You may adjust:

alpha in Wiener filter for noise control

k_exc_rel to tune excitation spatial frequency

📌 Notes

Only .tif or .tiff files with "angle" in the name are processed.

Phase extraction assumes a specific decimal format (e.g., Phase_0.071.tiff).

You can customize angle/phase lists if using non-standard SIM patterns.

📷 Example Visualization

Cropped Raw Image	SIM Reconstructed

(Optional: Add screenshots if available)

👨‍🔬 Author
Dr. Hassan Dibaji
Postdoctoral Researcher in Optical Imaging Systems
