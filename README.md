# pyfred
Python wrapper for Photon Engineering's FRED software

## Description
pyfred provides pythonic bindings into a FRED document and a consistent API
for using FRED through the win32 COM interface without having to worry about
the nuances and quirks associated with the raw win32 API.

Some advantages this provides are:

- Use of familiar Python idioms for scripting
- Availability of a vast amount of mature python libraries
- Interactive access to your model using the powerful IPython shell
- Use of the Jupyter Notebook for documentation, reporting and workflow

## Installation
pyfred is written and tested in Python 3.

pyfred has not yet been "packaged" so the installation process is
completely manual. The following instructions provide some helpful
guidelines but you will  need to be well versed in your own specific
python installation for troubleshooting purposes.

### Downloading
Currently pyfred is only available through GitHub. Grab the latest
version using
```bash
    $ git clone https://github.com/artdavis/pyfred
```
Alternatively, use a browser to navigate to
`https://github.com/artdavis/pyfred` and use the "Clone or download"
button to "download zip" and decompress into your folder of choice.

*IMPORTANT* The cloned or unzipped package will have within it a
subdirectory named `pyfred`. You should see python files in there like
`core.py`, `script00_verify_libraries.py` and others. It is this
directory which must be located inside of python's search path.
For example, if you have a project directory in your PYTHONPATH called
`C:\Users\username\Documents\python` you could put the pyfred directory
there: `C:\Users\username\Documents\python\pyfred`. Test that it works:
```bash
    $ python -c 'import pyfred'
```
If there are no reported errors then the path is good. If you get
a `ModuleNotFoundError` then you need to troubleshoot getting pyfred
into python's search path.


### Required libraries
pyfred requires the usual "scientific" library add-ons:
`numpy`, `scipy`, `matplotlib`, `IPython`, `win32com`, which will
typically be available if you've installed Python from a pre-packaged
distribution.

pyfred also requires:
* `PyYAML` - http://pyyaml.org/wiki/PyYAML

Preferably install missing packages using your primary package manager
assuming they're available there. Otherwise you may find and install
them via `pip`.

The availability of the necessary libraries can be tested by running
the included `script00_verify_libraries.py`. If this script runs with
no errors you are in good shape to move on to the next step.

### Building
pyfred must first build it's API from the FRED help file. It will look
in the most logical places, but if it can't find it, or you have a specific
version of a help file you want to use, you'll have to specify its location
manually (in `glovars.py` set `CHMAUTOLOCATE=False` and specify the location
of `Fred.chm` in `CHMPATH`).

Run the script0[1-3] files in order:

This first script decompiles the FRED help file for generating pyfred's API:
```bash
    $ python script01_winparse_chm.py
```

script02 creates the VBScript stub programs:
```bash
   $ python script02_stubgen.py
```

The third script wraps the FRED interface in python and creates pyfred's API:
```bash
    $ python script03_apiwrapgen.py
```

## License

pyfred is free software: you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

See LICENSE for details.

## Disclaimer
pyfred is not affiliated with Photon Engineering LLC.
