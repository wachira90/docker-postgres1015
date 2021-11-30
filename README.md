# docker-postgres1015
docker-postgres1015

## create data folder
````
mkdir data/
chmod -R 0777 data/
````

## run 
````
docker-compose up -d
````

## import example data
````
wget https://github.com/wachira90/docker-postgres1015/raw/main/dvdrental.zip

unzip dvdrental.zip

sudo cp dvdrental.tar data/dvdrental.tar

docker exec -it db pg_restore -U postgres -d dvdrental /var/lib/postgresql/data/dvdrental.tar
````

## images at
````
https://hub.docker.com/r/wachira90/postgres
````
