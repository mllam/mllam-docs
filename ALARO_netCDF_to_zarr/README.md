## Creating a zarr-like reference file for a collection of netCDF-files
This `notebook` is an example of how to use [kerchunk](https://fsspec.github.io/kerchunk/) to create a single `zarr`-like reference file for a collection of `netCDF`-files (living on the cloud).  

### Usage
If you want to run this notebook, you need to install `kerchunk` and its dependencies.  
You can create a `conda` environment using the `environment.yaml` file provided.
```
conda env create -f environment.yaml
```

### ALARO-data
A small subset of the ALARO data is publically available through the [LUMI S3 store](https://465001235.lumidata.eu/public).

