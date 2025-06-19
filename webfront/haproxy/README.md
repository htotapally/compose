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

curl -X POST "http://sclanetadm-PowerEdge-T110-II/os/create_payment_intent" -H "Content-Type: application/json" -d '%7B%22PB000001-5LB%22%3A%7B%22item%22%3A%7B%22ProductId%22%3A%22PB000001%22%2C%22ProduceName%22%3A%22Aashirvaad%20Select%20Whole%20Wheat%20Atta%22%2C%22Brand%22%3A%22Aashirvaad%22%2C%22Item%20Id%22%3A%22PB000001-5LB%22%2C%22Regular%20Price%22%3A6.99%2C%22Promotional%20Price%E2%80%9D%3A0%7D%2C%22qty%22%3A1%7D%7D%0A'
