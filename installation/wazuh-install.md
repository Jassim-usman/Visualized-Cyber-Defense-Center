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
