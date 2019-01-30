# dolibarr-docker
Docker stuff for Dolibarr deployement for Breizh'i Coop NGO.

## docker-compose.yml

* based on Dolibarr's [tuxgasy Docker image](https://hub.docker.com/r/tuxgasy/dolibarr) and compatible MariaDB Docker image
* additionnal Adminer Docker image is included but **should be removed later**
* Volumes
	* create a named volume for database
	* other volumes are Dolibarr flat files (documents, templates) and custom apps dir
* uses `.env` file for `environment` vars

REMARKS:

* for importing existing database, don't know how to do other way than:
	* launching empty instance
	* flushing database
	* import database

Probably necessary to write an `entrypoint` script...


TODO:

* move Dolibarr's instance to public network if necessary
* remove Adminer instance

## Dockerfile

Have been tested :

* [Official Docker image](https://github.com/Dolibarr/dolibarr/tree/develop/build/docker) : **KO** with mysqli error
* [monogramm](https://hub.docker.com/r/monogramm/docker-dolibarr) : **KO** with mysqli error. Tested versions:
	* `8.0.4-php7.1-apache`, `8.0.4-apache`, `8.0.4-php7.1` and `8.0.4`
	* `8.0.4-php7.1-alpine`
	* `8.0.4-php5.6-apache`
* [tuxgasy](https://hub.docker.com/r/tuxgasy/dolibarr) : **OK** (this one)
	* `8.0.4-php7.1 ` : **KO**
	* `8.0.4-php7.0` : **OK**