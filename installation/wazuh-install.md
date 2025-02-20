# Wazuh Installation Guide


Wazuh provides a pre-built virtual machine image in Open Virtual Appliance
(OVA) format. This can be directly imported to VirtualBox or other OVA
compatible virtualization systems.
Download the virtual appliance (OVA), which contains the following
components:

- Wazuh manager 4.9.0
- Wazuh indexer 4.9.0
- Filebeat-OSS 7.10.2
- Wazuh dashboard 4.9.0

# Hardware requirements:

The following requirements have to be in place before the Wazuh VM can be
imported into a host operating system:

- The host operating system has to be a 64-bit system.
- Hardware virtualization has to be enabled on the firmware of the host.
- A virtualization platform, such as VirtualBox, should be installed on the
  host system.
# Installation in virtual machine:

1. Import the OVA to the virtualization platform.
2. If you're using VirtualBox, set the VMSVGA graphic controller. Setting
   another graphic controller freezes the VM window.
    - Select the imported VM.
    - Click Settings > Display
    - In Graphic controller, select the VMSVGA option.
3. Start the machine.
4. Access the virtual machine using the following user and password. You can
   use the virtualization platform or access it via SSH.

                      user: wazuh-user
                      password: wazuh

SSH root user login has been deactivated; nevertheless, the wazuh-user
retains sudo privileges. Root privilege escalation can be achieved by
executing the following command:

                     sudo -i

# Access the Wazuh dashboard:
1. Shortly after starting the VM, the Wazuh dashboard can be accessed from
the web interface by using the following credentials:

                 URL: https://<wazuh_server_ip>
                 user: admin
                 password: admin

2. You can find <wazuh_server_ip> by typing the following command in the
   VM:

                      ip a

# Configuration files:

All components included in this virtual image are configured to work out-of-the-
box, without the need to modify any settings. However, all components can be
fully customized. These are the configuration files locations:

1. Wazuh manager: /var/ossec/etc/ossec.conf
2. Wazuh indexer: /etc/wazuh-indexer/opensearch.yml
3. Filebeat-OSS: /etc/filebeat/filebeat.yml
4. Wazuh dashboard:
   - /etc/wazuh-dashboard/opensearch_dashboards.yml
   - /usr/share/wazuh-dashboard/data/wazuh/config/wazuh.yml
