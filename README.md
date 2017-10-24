# Docker Compose wordpress

## Usage

### Start the proxy

- Create a bridge network

```bash
docker network create traefik
```

- Launch the proxy

```bash
cd proxy
docker-compose up -d
```

### Start the sites

- go to site directory

```bash
cd site
```


- start site with hostname `site1.net`

```bash
export VHOST=site1.net
docker-compose -p $VHOST up -d
```


- scale `site1.net` to 3 servers

```bash
docker-compose -p $VHOST scale wordpress=3
```


- start site with hostname `site2.net`

```bash
export VHOST=site2.net
docker-compose -p $VHOST up -d
```


- show logs from specific hostname

Example fot site1.net
```bash
docker-compose -p site1.net logs -f
```

- customise the db password

On creation :
```bash
export VHOST=site3.net
export DB_NAME=mycustomdbname
export DB_USER=mycustomuser
export DB_PASS=mycustompassword

docker-compose -p $VHOST up -d
```


