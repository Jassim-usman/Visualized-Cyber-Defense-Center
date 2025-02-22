# openVAS Installation Guide

# PREREQUISITES:

Before proceeding with the installation, ensure that the following program is
already installed on your system:

1. Ubuntu 20.04/22.04
# UPDATE SYSTEM:

              sudo apt update && sudo apt upgrade -y

# INSTALL OPENVAS:

              sudo apt install -y gvm

# SETUP OPENVAS:

              sudo gvm-start

# GET ADMIN CREDENTIALS:

1. To retrieve the default admin password:

                https://127.0.0.1:9392

2. Use the credentials obtained earlier to log in.

# Running and Using OpenVAS:

Once installed and running, follow these steps to perform a vulnerability scan:

1. Log in to the Web UI at https://127.0.0.1:9392.
2. Create a Target: Go to Configuration → Targets and define the IP range you
   want to scan.
3. Start a Scan: Navigate to Scans → Tasks and create a new task.
4. Analyze Results: After the scan completes, view the report under Scans →
   Reports.
