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

