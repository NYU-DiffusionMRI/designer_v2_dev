---
layout: default
title: Installation
parent: designer
has_children: false
nav_order: 1
---

# Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Installing DESIGNER version 2

The new version of designer consists of a number of updates and improvements to the original implementation. Designer version 2 is written in python and c++ and is an external [Mrtrix3](https://www.mrtrix.org) project.

Designer its dependencies can be installed in one line using pip: 
```
pip install designer2
```

To upgrade designer to the newest version after it has already been installed, just use the command:
```
pip install --upgrade designer2
```


## Requirements and Dependencies
Currently, designer requires a source installation of mrtrix3 in order to run. A future update of the mrtrix3 precompiled binaries may eliminate these requirements, however as of today, users must follow the steps [here](https://mrtrix.readthedocs.io/en/latest/installation/build_from_source.html) to configure and build the source mrtrix3 package. 

We recommend installing the `dev` branch as well, as there are additional features in `dwifslpreproc` that have no yet made it to the main codebase. The source mrtrix3 installation can be completed by running the following lines after ensuring that mrtrix3 dependencies are installed properly.
```
git clone https://github.com/MRtrix3/mrtrix3.git
cd mrtrix3
git checkout dev
./configure
./build
```

After mrtrix3 has been successfully installed, users should create the `PYTHONPATH` environment variable and link it against the mrtrix3 python libraries:
```
export PYTHONPATH=</path/to/mrtrix3/lib>
```

For example, if a user clones the mrtrix3 github repository to the directory `/usr/local/mrtrix3`, they would run the command `export PYTHONPATH=/usr/local/mrtrix3/lib`. We recommend that users add this line to their `.bashrc` or `.bash_profile` so that designer is permanently configured properly in the users shell environment.

---

Designer also relies on FSL tools for EPI distortion correction and eddy current and motion correction. Users can install FSL [here](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslInstallation) and follow the steps outlined in the FSL documentation.

---

In addition to Mrtrix3 and FSL, designer should automatically install a number of additional python dependencies including:
- numpy
- scipy
- numpy_groupies
- antspyx (for MRI image i/o)
- dipy (diffusion denoising using patch2self)
- tqdm
- joblib
- cvxpy
- pandas

We recommend that users keep python and pip as up-to-date as possible to ensure that Designer runs smoothly. Designer was originally written in Python 3.9 and is known to be compatible with versions as low as Python 3.7 and up to 3.11. We also recommend that users run Designer within a python environment such as [conda](https://www.anaconda.com), [pyenv](https://github.com/pyenv/pyenv), or whichever you prefer. The choice of environment is up to the user, however environments are useful to manage potential dependency conflict.

{: .warning }
There is a known [issue](https://github.com/conda/conda/issues/12051) in conda environments on windows and Ubuntu that can prevent the installation of `designer`. The fix is to install `numpy-base` before running the `pip install designer2` command.


