This is a part of pytorch3D library. It is suitabale for installing on colab.
I meann it has lower installing time to use just essential files.

%cd /content/PD-LTS/ex

# !rm -rf build dist *.egg-info
# !rm -rf mytorch3d/*.so

!python setup_p.py develop
# !python setup.py install

import os
import sys
import torch

# Add PyTorch lib directory to system path
torch_lib_path = os.path.join(os.path.dirname(torch.__file__), 'lib')
if 'LD_LIBRARY_PATH' in os.environ:
    os.environ['LD_LIBRARY_PATH'] = f"{torch_lib_path}:{os.environ['LD_LIBRARY_PATH']}"
else:
    os.environ['LD_LIBRARY_PATH'] = torch_lib_path

# Also try adding it directly to the system path
if torch_lib_path not in sys.path:
    sys.path.append(torch_lib_path)


# Now try importing
# import mytorch3d
# from mytorch3d import _C

import pytorch3d
from pytorch3d import _C

!pip install git+https://github.com/otaheri/chamfer_distance@f86f6f7cadd3aca642704573d1626c67ca2e2846

# with 6 min
