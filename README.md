PyTorch3D Minimal Setup for Google Colab
This repository provides an optimized setup for using essential components of the PyTorch3D library on Google Colab. The setup is designed to minimize installation time while ensuring compatibility with custom extensions like the Chamfer Distance implementation.

Installation Guide
Follow these steps to set up the environment in Google Colab:

Step 1: Clone the Repository and Navigate
bash
Copy code
%cd /content/PD-LTS/ex
Step 2: Build and Develop the Custom PyTorch3D Library
bash
Copy code
!python setup_p.py develop


# Locate PyTorch's library directory
torch_lib_path = os.path.join(os.path.dirname(torch.__file__), 'lib')

# Update LD_LIBRARY_PATH
if 'LD_LIBRARY_PATH' in os.environ:
    os.environ['LD_LIBRARY_PATH'] = f"{torch_lib_path}:{os.environ['LD_LIBRARY_PATH']}"
else:
    os.environ['LD_LIBRARY_PATH'] = torch_lib_path

# Add to Python system path
if torch_lib_path not in sys.path:
    sys.path.append(torch_lib_path)
Step 4: Install the Chamfer Distance Implementation
Install the Chamfer Distance library from the specific GitHub commit:

bash
Copy code
!pip install git+https://github.com/otaheri/chamfer_distance@f86f6f7cadd3aca642704573d1626c67ca2e2846
Usage Example
After setting up the environment, you can import and use PyTorch3D along with the Chamfer Distance library:

python
Copy code
import pytorch3d
from pytorch3d import _C  # Import core PyTorch3D functionality

# Example usage for Chamfer Distance
from chamfer_distance import ChamferDistance
chamfer = ChamferDistance()
Notes
This setup is optimized for Colab to reduce installation time (approximately 10 minutes).
If you encounter issues with missing dependencies, ensure that PyTorch and CUDA are properly installed on your Colab environment.
For extended functionality, consider using the full version of PyTorch3D.
Feel free to contribute or raise issues in case of questions or improvements!
