# Odoo 18 Docker

### Prerequisite

Before you begin, ensure you have installed:
- [Docker Community Edition (Docker-CE)](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)


Project File Structure
```
Odoo18-Docker
├── docker-compose.yml # Docker Compose configuration file 
├── .env # Environment variables (credentials, etc.) 
└── odoo/  
    ├── config/ # Odoo configuration files (e.g., odoo.conf) 
    ├── addons/ # Custom Odoo addons 
    └── enterprise/ # Enterprise Modules 
```

### Docker Compose Commands
Here are some useful commands for managing your deployment:

- Start Containers in Foreground:
```
docker-compose up 
```
- Start Containers in Detached Mode:
```
docker-compose up -d
```
- Rebuild Containers (after configuration changes):
```
docker-compose up --build
```
- Restart all services:
```
docker-compose restart
```
- Stop All Services:
```
docker-compose stop
```
- Remove All Containers and Networks:
```
docker-compose down
```

### Useful Docker Commands
 
>Access the Odoo container shell:
```
docker exec -it <container name> <command> 
```

> Navigate to command-line utility of the container
```
docker exec -it odoo_18 /bin/bash 
```

> Update all Odoo Module
1. Restart the web services.
```
docker-compose restart web
```

2. Run the update command (replace <db_name> with your database name):
```
docker exec -it odoo_18 odoo -d <db_name> --db_host db -r odoo18 -w odoo18 -u all --stop-after-init
```

> Launch the Odoo Shell for Interactive Debugging:
```
docker exec -it odoo_18 odoo shell -d <db_name> --db_host db -r odoo18 -w odoo18 
```