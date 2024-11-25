# Custom PyTorch3D and Dependencies Setup for Colab

## Overview
This setup script provides a streamlined method to install PyTorch3D and related dependencies in Google Colab with minimal installation time and optimized configuration.

## Prerequisites
- Google Colab environment
- Python 3.8+
- PyTorch installed

## Installation Steps

### 1. Clone the Repository
```bash
git clone https://github.com/your-repo/PD-LTS.git
cd PD-LTS/ex
```

### 2. Setup Script
The installation script performs several key actions:
- Configures PyTorch library paths
- Sets up environment variables
- Installs custom extensions
- Adds Chamfer Distance package

### 3. Installation Code
```python
import os
import sys
import torch

# Add PyTorch lib directory to system path
torch_lib_path = os.path.join(os.path.dirname(torch.__file__), 'lib')

# Configure LD_LIBRARY_PATH
if 'LD_LIBRARY_PATH' in os.environ:
    os.environ['LD_LIBRARY_PATH'] = f"{torch_lib_path}:{os.environ['LD_LIBRARY_PATH']}"
else:
    os.environ['LD_LIBRARY_PATH'] = torch_lib_path

# Add torch library path to system path
if torch_lib_path not in sys.path:
    sys.path.append(torch_lib_path)

# Optional: Development mode installation
# python setup_p.py develop
# python setup.py install

# Install Chamfer Distance
!pip install git+https://github.com/otaheri/chamfer_distance@f86f6f7cadd3aca642704573d1626c67ca2e2846
```

## Cleanup (Optional)
To clean previous builds:
```bash
rm -rf build dist *.egg-info
rm -rf mytorch3d/*.so
```

## Common Issues
- Ensure you have the latest PyTorch version
- Check that all dependencies are compatible
- Verify CUDA and GPU settings if using GPU acceleration

## Dependencies
- PyTorch
- Chamfer Distance package

## Contributing
Contributions are welcome! Please submit pull requests or open issues for any improvements or bug fixes.

## License
[Add your license information here]

## Contact
[Add contact information or project maintainer details]
