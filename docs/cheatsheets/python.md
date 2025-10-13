# Work with Python 

## Set up & activate the Python environment
[NVIDIA documentation](https://nvidia-omniverse.github.io/LearnOpenUSD/usdview-install-instructions.html)

### Create Python venv

```powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\usd_root> .\python\python.exe -m venv .\python-usd-venv
```

### Activate Python venv

```powershell
PS C:\usd_root> .\python-usd-venv\Scripts\activate
(python-usd-venv) PS C:\usd_root>

```

### Install and test USD Core

```powershell

(python-usd-venv) PS C:\usd_root>pip install usd-core

(python-usd-venv) PS C:\usd_root>python -c "from pxr import Usd;print(Usd.GetVersion())"

```

If an error occurs, you may need to install the VC Redistributables:

[x64 Redistributables](https://aka.ms/vs/17/release/vc_redist.x64.exe),
see 
[Microsoft Support](https://learn.microsoft.com/de-de/cpp/windows/latest-supported-vc-redist?view=msvc-170)

### Install Jupyter Notebook support


```powershell
(python-usd-venv) PS C:\usd_root> pip install ipykernel

Then restart Visual Studio Code

#### Enable the VS Code Jupyter extension 
(search for "Jupyter" in Extensions)

#### Test:

View -> Command Palette -> Create: New Jupyter Notebook
