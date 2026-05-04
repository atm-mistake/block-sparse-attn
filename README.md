# Block Sparse Attention (Custom CUDA Extension) For Linux Python 3.11 PyTorch 2.6.0+cu124 CUDA 12.4

block_sparse_attn-0.0.1-cp311-cp311-linux_x86_64.whl

This is a pre-compiled custom CUDA extension for Block Sparse Attention, I used it on google colab so i decided to share it for you to save time. 

**Environment Requirements:**
* **OS:** Linux (x86_64)
* **Python:** 3.11 
* **PyTorch:** 2.6.0+cu124
* **CUDA:** 12.4

Because CUDA extensions are highly sensitive to Python and PyTorch versions, this wheel is strictly compiled for **Python 3.11** and **CUDA 12.4**. If your system uses a different default Python version, we highly recommend setting up an isolated environment. 

Below are the exact steps to create a compatible environment using `micromamba` (a fast, lightweight conda alternative) and install the pre-compiled wheel.

## Installation

Run these commands in your Linux terminal to set up the environment and install the extension without compiling from source.

**1. Install Micromamba & Create Environment**
```bash
# Download micromamba to the local directory
curl -Ls [https://micro.mamba.pm/api/micromamba/linux-64/latest](https://micro.mamba.pm/api/micromamba/linux-64/latest) | tar -xj bin/micromamba

# Create and activate a fresh Python 3.11 environment
./bin/micromamba create -n py311 python=3.11 -c conda-forge -y
```
**2. Define Dependencies**
We specify the cu124 PyTorch wheels to ensure compatibility with this extension,
Before you install your requirements.txt you need to rewrite it, eg:
```bash
%%writefile requirements.txt
torch==2.6.0+cu124
torchaudio==2.6.0+cu124
torchvision==0.21.0+cu124
accelerate==1.8.1
transformers==4.46.2
xformers
einops==0.8.1
# Add any other specific packages your project needs
```

**3. Install Dependencies & The Custom Wheel**
```bash
# Install the requirements using the PyTorch CUDA 12.4 index
./bin/micromamba run -n py311 pip install -r requirements.txt --extra-index-url [https://download.pytorch.org/whl/cu124](https://download.pytorch.org/whl/cu124)

# Download and install the pre-compiled custom wheel directly from GitHub Releases
./bin/micromamba run -n py311 pip install [https://github.com/atm-mistake/YOUR_REPO_NAME/releases/download/v0.0.1/block_sparse_attn-0.0.1-cp311-cp311-linux_x86_64.whl](https://github.com/atm-mistake/block-sparse-attn/releases/download/v0.0.1/block_sparse_attn-0.0.1-cp311-cp311-linux_x86_64.whl)
```
**4. Running Python Scripts**
When you need to execute your .py scripts inside this new environment, simply prefix your command with ```./bin/micromamba run -n py311 run```:
```python
./bin/micromamba run -n py311 {command}
```

📜 Acknowledgements & License:
Micromamba: Environment management in these instructions uses Micromamba, an open-source tool by mamba-org.
License: This project is licensed under the MIT License - see the LICENSE file for details.
