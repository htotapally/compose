Override configuration parameters in haproxy.cfg

For example using the servername replaceme.example.com.  This server name should be an internal name, and should not be exposed to internet.


Update /etc/hosts  
Make an entry for replaceme.example.com    
192.168.1.170   replaceme.example.net   replaceme  

Proxy server testing  
On the server open a terminal.  Execute a series of curl commands to ensure all services are functional.

Testing sml-apach2 container  
curl http://localhost/  
curl http://replaceme/  
curl http://replaceme.example.net/  
curl http://replaceme.example.net:8081/  

should return contents of index.html from public-html  


Testing product service  
curl http://localhost/cp  
curl http://replaceme/cp  
curl http://replaceme.example.net/cp  

should return ProductService is Alive  


Testing order service  

curl http://localhost/os  
curl http://replaceme/os  
curl http://replaceme.example.net/os  

should return OrderService  

curl http://replaceme.example.net/os/getorders  
should return [], if there were no orders were created.  Otherwise should return all unprocessed orders.

curl -X POST "http://sclanetadm-PowerEdge-T110-II/os/create_payment_intent"  -d '%7B%20%22PB000001-5LB%22%3A%20%7B%20%22ProductId%22%3A%22PB000001%22%2C%20%22ProduceName%22%3A%22Aashirvaad%20Select%20Whole%20Wheat%20Atta%22%2C%20%22Brand%22%3A%22Aashirvaad%22%2C%20%22Item%20Id%22%3A%22PB000001-5LB%22%2C%20%22Regular%20Price%22%3A6.99%2C%20%22Promotional%20Price%22%3A0%20%7D%2C%20%22qty%22%3A1%20%7D'


curl -X POST "http://sclanetadm-PowerEdge-T110-II/os/create_payment_intent" -H "Content-Type: application/json" -d '{ "PB000001-5LB": { "ProductId":"PB000001" }, "qty":1 }'


curl -X POST "http://sclanetadm-PowerEdge-T110-II/os/create_payment_intent" -H "Content-Type: application/json" -d '{ "PB000001-5LB": { "ProductId":"PB000001", "ProduceName":"Aashirvaad Select Whole Wheat Atta", "Brand":"Aashirvaad", "Item Id":"PB000001-5LB", "Regular Price":6.99, "Promotional Price":0 }, "qty":1 }'

curl -H "Content-Type: application/json" --data @body.json http://localhost:8080/ui/webapp/con

curl -H "Content-Type: application/json" --data @ci.json http://sclanetadm-PowerEdge-T110-II/os/create_payment_intent

curl -H "Content-Type: application/json" --data-urlencode   '{ "PB000001-5LB": { "ProductId":"PB000001", "ProduceName":"Aashirvaad Select Whole Wheat Atta", "Brand":"Aashirvaad", "Item Id":"PB000001-5LB", "Regular Price":6.99, "Promotional Price":0 }, "qty":1 }' http://sclanetadm-PowerEdge-T110-II:8090/create_payment_intent

 curl  --data-urlencode  '%7B%20%22PB000001-5LB%22%3A%20%7B%20%22ProductId%22%3A%22PB000001%22%2C%20%22ProduceName%22%3A%22Aashirvaad%20Select%20Whole%20Wheat%20Atta%22%2C%20%22Brand%22%3A%22Aashirvaad%22%2C%20%22Item%20Id%22%3A%22PB000001-5LB%22%2C%20%22Regular%20Price%22%3A6.99%2C%20%22Promotional%20Price%22%3A0%20%7D%2C%20%22qty%22%3A1%20%7D' -v -H "Content-Type: application/json"  http://sclanetadm-PowerEdge-T110-II:8090/create_payment_intent


 export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')

 
 
