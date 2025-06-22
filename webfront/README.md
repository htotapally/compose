# Update environment specific configuration files

## 1. ordsvc/ordsvc.conf

## 2. ordsvc/webserver.conf

Replace ordersurl, kafka topic name, and kafka bootstrap end points

## 2. prodprovider/dcos.json

## 3. prodprovider/webserver.conf

# Services needed for running web front end  

compose.yml deploys required images by overriding the override configurations as defined in docker-compose.yml  

Pull latest images from docker registry  
```
docker compose pull  
```
To launch the containers in detached run the command:    
```
docker compose up -d  
```
To stop the containers run the command:  
```
docker compose stop  
```

To delete the containers run the command:  
```
docker compose down  
```

