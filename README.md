Heroku Buildpack: Geo + Apt
=====================

This is a **very wonky** buildpack for Heroku, which install geolibraries and also reads Aptitude files (for installing dependencies such as OpenCV).
I won't be maintaining this except when I need to (i.e.: someday update to GDAL 3+ and do tests properly).


Usage
-----

**NOTE:** If installing Python GDAL, choose to use pygdal==2.4.0.4 instead of the normal gdal library at requirement.txt. The former uses numpy as dependency.
**NOTE:** If installing Python OpenCV, you should leave libgl1, libsm6, libxrender1, libfontconfig1, libice6 at your Aptitude file and then python-opencv at requirements.txt.


Also, ensure that this buildpack is the first buildpack on your list of buildpacks:

```
$ heroku buildpacks
=== Buildpack URLs
1. https://github.com/raijenki/heroku-geo-buildpack.git
2. heroku/python
```

Default Versions
----------------

The buildpack will install the following version by default:

GDAL - 2.4.0</br>
GEOS - 3.7.2</br>
PROJ - 5.2.0</br>

You can change the version of each library that will be installed by setting the `GDAL_VERSION`, `GEOS_VERSION` or `PROJ_VERSION` config variables.
