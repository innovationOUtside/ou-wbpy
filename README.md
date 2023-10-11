# ou-wbpy

Slight fork of / wrapper for `wbpy` for use in JupyterLite / OpenLearn Learn to Code for Data Analysis.

Usage:

```python
from ou_wbpy.api import wbapi

api = wbapi()
api.get_dataframe("SP.POP.TOTL", date="2010:2012")

```

Uses pyodide load machinery in Pyodide JupyterLite kernel (detected by trying `import pyodide`, else uses normal Python url loaders).


## Using `pandas-datareader`

I originally hacked `ou-wbpy` from reviewing all the World Bank API reading packaged I found whilst looking for a replacement for the [`pandas-datareader`](pandas-datareader) package (which was originally pulled out of the main `pandas` package), which doesn't work out of the can in Pyodide.

But - it does, with a patch...

```python
#Install package and its requirements
%pip install pandas_datareader distutils

#Patch various common packages
try:
  import pyodide_http
  pyodide_http.patch_all()
except:
  pass

from pandas_datareader import wb

wb.download(indicator='NY.GDP.PCAP.KD', country=['US', 'CA', 'MX'], start=2005, end=2008)
```
