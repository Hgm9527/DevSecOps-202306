# https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elastic-stack-on-ubuntu-22-04

# https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-22-04

# https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-22-04


# The Elastic Stack has four main components:

Elasticsearch: a distributed RESTful search engine which stores all of the collected data.
Logstash: the data processing component of the Elastic Stack which sends incoming data to Elasticsearch.
Kibana: a web interface for searching and visualizing logs.
Beats: lightweight, single-purpose data shippers that can send data from hundreds or thousands of machines to either Logstash or Elasticsearch.

# Setup:

# Java

1) sudo apt update
2) sudo apt install default-jre
3) sudo apt install default-jdk
4) sudo update-alternatives --config java\

# Nginx

1) sudo apt update
2) sudo apt install nginx
3) sudo ufw app list
4) sudo ufw allow 'Nginx HTTP'


# ElasticSearch
1) curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch |sudo gpg --dearmor -o /usr/share/keyrings/elastic.gpg
2) echo "deb [signed-by=/usr/share/keyrings/elastic.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list

3) sudo apt update
4) sudo apt install elasticsearch

5) sudo nano /etc/elasticsearch/elasticsearch.yml
    uncomment network values -> port and host -> localhost

6) curl -X GET "localhost:9200"
7) sudo systemctl start elasticsearch
7) sudo systemctl enable elasticsearch


# Kibana
1) sudo apt install kibana
2) sudo systemctl enable kibana
3) sudo systemctl start kibana
4) echo "kibanaadmin:`openssl passwd -apr1`" | sudo tee -a /etc/nginx/htpasswd.users
Rayadmin123

kibanaadmin:$apr1$sxzPX9QH$itX7FUuxXkGni.eDwKAsB0

5) sudo nano /etc/nginx/sites-available/www.s3-saanvi-sri-sai.co.in
   http://www.s3-saanvi-sri-sai.co.in/

6) sudo ln -s /etc/nginx/sites-available/s3-saanvi-sri-sai.co.in /etc/nginx/sites-enabled/s3-saanvi-sri-sai.co.in

7) sudo nginx -t

8) sudo systemctl reload nginx

9) sudo ufw allow 'Nginx Full'

10) sudo ufw delete allow 'Nginx HTTP'



#
   









