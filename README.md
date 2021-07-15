# Docker for geospatial utils

## Description
As of today, include GDAL, PDAL and PROJ libs
Versions of each libs is set in the .env file, run the following command to check containers 
version pulled

```
cat .env
```
you can downgrade or upgrade the version by modifying this .env file.

You can also setup a GIS_DATA var pointing to a folder that will be mounted in the docker images as volume (RW)

## Usage

Go to the geoutils folder and simply run the following command:

```
docker-compose up -d
```
you can also use the -f arg to point to the docker-compose.yml file of the geoutils repo cloned

```
docker-compose -f <PATH_TO_CLONED_GEOUTILS> up -d
```

Once container started, if you want to use a gdal tool, just run the following command:

```
docker exec -it $(docker ps | egrep geoutils_gdal | awk '{print $1}') gdalinfo --version
```

Once container started, if you want to use a pdal tool:
```
docker exec -it $(docker ps | egrep geoutils_pdal | awk '{print $1}') pdal --version
```

Once container started, if you want to use a proj tool
```
docker exec -it $(docker ps | egrep geoutils_proj | awk '{print $1}') proj
```

