# THEHIVE Installation Guide

## PREREQUISITES:

1. Open a terminal window.
2. Run the following command to install the necessary dependencies:

                 apt install wget gnupg apt-transport-https git ca-certificates ca-certificates-java curl software-
                 properties-common python3-pip lsb-release

Ensure that all dependencies are successfully installed before proceeding with
the TheHive installation process.

# Java Virtual Machine:

           wget -qO- https://apt.corretto.aws/corretto.key | sudo gpg --dearmor -o
           /usr/share/keyrings/corretto.gpg

           echo "deb [signed-by=/usr/share/keyrings/corretto.gpg] https://apt.corretto.aws stable main" |
           sudo tee -a /etc/apt/sources.list.d/corretto.sources.list

           sudo apt update
           
           sudo apt install java-common java-11-amazon-corretto-jdk

           echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment

           export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"

3. Verify the installation by running:

            java -version

4. You should see output similar to the following:

            openjdk version "11.0.12" 2022-07-19

            OpenJDK Runtime Environment Corretto-11.0.12.7.1 (build 11.0.12+7-LTS)

            OpenJDK 64-Bit Server VM Corretto-11.0.12.7.1 (build 11.0.12+7-LTS, mixed mode)

 #  Apache Cassandra Installation:

Apache Cassandra is a highly scalable and robust database system. TheHive is
fully compatible with Apache Cassandra's latest stable release version 4.0.x.

1. Add Apache Cassandra repository references:
   - Download Apache Cassandra repository keys using the following command:
  
            wget -qO - https://downloads.apache.org/cassandra/KEYS | sudo gpg --dearmor -o
            /usr/share/keyrings/cassandra-archive.gpg

   - Add the repository to your system by appending the following line to the
    /etc/apt/sources.list.d/cassandra.sources.list file. This file may not exist, and
    you may need to create it.

            echo "deb [signed-by=/usr/share/keyrings/cassandra-archive.gpg]
            https://debian.cassandra.apache.org 40x main" | sudo tee -a

  2. Install the package:

      - Once the repository references are added, update your package index and
        install Cassandra using the following commands:

                         sudo apt update

                         sudo apt install cassandra

     - By default, data is stored in/var/lib/cassandra. Ensure appropriate
       permissions are set for this directory to avoid any issues with data storage
       and access.

# Configuration:

You can configure Cassandra by modifying settings within the
/etc/cassandra/cassandra.yaml file.
1. Locate the Cassandra Configuration File:
  - Navigate to the directory containing the Cassandra configuration file
    /etc/cassandra/

2. Edit the cassandra.yaml File:
  - Open the cassandra.yaml file in a text editor with appropriate permissions.

3. Configure Cluster Name:
   - Set the cluster_name parameter to the desired name. This name helps identify
     the Cassandra cluster.

4. Configure Listen Address:
   - Set the listen_address parameter to the IP address of the node within the
     cluster. This address is used by other nodes within the cluster to
     communicate.

5. Configure RPC Address:
   - Set the rpc_address parameter to the IP address of the node to enable clients
     to connect to the Cassandra cluster.

6. Configure Seed Provider:
   - Ensure the seed_provider section is properly configured. The seeds parameter
     should contain the IP address(es) of the seed node(s) in the cluster.

7. Configure Directories:
   - Set the directories for data storage, commit logs, saved caches, and hints as
     per your requirements. Ensure that the specified directories exist and have
     appropriate permissions.

8. Save the Changes:
   - After making the necessary configurations, save the changes to the
     cassandra.yaml file.
