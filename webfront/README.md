# Update environment specific configuration files

## 1. ordsvc/ordsvc.conf
Update stripe.api_key with assigned one.
```
[global]
server.socket_host = 0.0.0.0
server.socket_port = 8090
server.thread_pool = 10

['/']
request.dispatch = cherrypy.dispatch.MethodDispatcher()
'cors.expose.on': True
'tools.response_headers.headers': [('Content-Type', 'image/jpeg'), ('Access-Control-Allow-Origin', '*')]

[stripe]
stripe.api_key = sk_test_BQokikJOvBiI2HlWgH4olfQ2
```

## 2. ordsvc/webserver.conf

Replace ordersurl, kafka topic name, and kafka bootstrap end points

## 3. prodprovider/docs.json
Update documents.

## 4. prodprovider/webserver.conf

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
To debug issues with a service defined in compose.yml
```
docker compose run -e DEBUG=true <service in compose.yml>
```

# Accessing Webfront
The website is accessible using the url http://<hostname/

