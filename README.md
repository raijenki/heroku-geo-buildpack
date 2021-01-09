Heroku Buildpack: Geo + Apt
=====================

This is a **very wonky** buildpack for Heroku, which install geolibraries and also reads Aptitude files (for installing dependencies such as OpenCV). It's essentialy a copy-paste work from heroku/heroku-geo-buildpack and heroku/heroku-buildpack-apt.

I won't be maintaining this except when I need to (i.e.: someday update to GDAL 3+ if I require at Heroku and do tests properly).


Usage
-----

Ensure that this buildpack is the first buildpack on your list of buildpacks:

```
$ heroku buildpacks
=== Buildpack URLs
1. https://github.com/raijenki/heroku-geo-buildpack-apt.git
2. heroku/python
```

Also, you should have a file named `Aptfile` which lists all apt dependencies for installation. This is done before the installation of geolibraries.

**NOTE:** If installing Python GDAL, choose to use `pygdal==2.4.0.4` instead of the normal `gdal` library at requirements.txt. The former uses `numpy` as dependency, so you won't have issues with gdal_arrays.

**NOTE 2:** If installing Python OpenCV, you should use `libgl1`, `libsm6`, `libxrender1`, `libfontconfig1`, `libice6` at your `Aptfile` and then `python-opencv` at requirements.txt.




Default Versions
----------------

The buildpack will install the following version by default:

GDAL - 2.4.0</br>
GEOS - 3.7.2</br>
PROJ - 5.2.0</br>

You can change the version of each library that will be installed by setting the `GDAL_VERSION`, `GEOS_VERSION` or `PROJ_VERSION` config variables.
