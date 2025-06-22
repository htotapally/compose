Update environment specific configuration files  

orderdispatcher/dispconf.conf
Replace ordersurl, kafka topic name, and kafka bootstrap end points  

[orders]  
ordersurl = http://192.168.1.170/os/getorders  

[kafka]  
topic = TutorialTopic  
bootstrap = ["192.168.1.170:9092"]  


orderstatusupdate/dispconf.conf
Replace orderupdateurl, kafka topic name, and kafka bootstrap end points  

[orders]  
orderupdateurl = http://192.168.1.170/os/complete  

[kafka]  
topic = OrderStatus  
bootstrap = ["192.168.1.170:9092"]  



Services needed for running web front end  

compose.yml deploys required images by overriding the override configurations as defined in docker-compose.yml  

Pull latest images from docker registry  
docker compose pull  

To launch the containers in detached run the command:    
docker compose up -d  

To stop the containers run the command:  
docker compose stop  

To delete the containers run the command:  
docker compose down  


