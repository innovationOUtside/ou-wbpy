# ou-wbpy

Slight fork of `wbpy` for use in JupyterLite / OpenLearn Learn to Code for Data Analysis.

Usage:

```python
from ou_wbpy.api import wbapi

api = wbapi()
api.get_dataframe("SP.POP.TOTL", date="2010:2012")

```

Uses pyodide load machinery in Pyodide JupyterLite kernel (detected by trying `import pyodide`, else uses normal Pyhton url loaders).
