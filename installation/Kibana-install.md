# Kibana Installation Guide

# PREREQUISITES:

--Before installing Kibana, ensure that you have the necessary dependencies,
  including Node.js and Elasticsearch. Ensure Elasticsearch is running and
  accessible.

                    sudo apt-get update

                    sudo apt-get install -y wget

# Install Kibana:

--Go to the Kibana downloads page and find the version that matches your
  Elasticsearch version. Use wget to download it.

                    sudo dpkg -i kibana-7.17.12-amd64.deb

# Configure Kibana:

1. Edit the Kibana Configuration File:
   --Open the kiban
   a.yml configuration file, usually located in /etc/kibana.

                    sudo nano /etc/kibana/kibana.yml

3. Set the Elasticsearch URL:
   --Uncomment and set the Elasticsearch URL. Replace localhost with the IP
     address of your Elasticsearch server if it’s not on the same machine.

                    elasticsearch.hosts: ["http://localhost:9200"]

4. Set the Server Host and Port:
   --You can set the server host and port as needed. For local access, you might
     set:

                    server.host: "0.0.0.0"

                    server.port: 5601

# Start Kibana:

1. Start the Kibana service using the following command:

                   sudo systemctl start kibana

2. Enable Kibana on Boot:
   --To ensure Kibana starts automatically on boot, enable the service:

                   sudo systemctl enable kibana

# Access Kibana:

  --Open your web browser and go to http://<your_kibana_ip>:5601. You should
    see the Kibana interface.
