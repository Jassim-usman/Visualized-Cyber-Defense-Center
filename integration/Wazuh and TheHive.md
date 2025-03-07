# Wazuh and TheHive Integration Guide

# Prepare TheHive:

1. Create a new organization on TheHive web interface and with an administrator account.
2. In Test Organization, we create a new user with organization administrator privileges.
3. This user has permissions to manage the organization, including creating new users,
   managing cases, and alerts, amongst others.
4. We also create a password for this user so that we can log in to view the dashboard and
   manage cases.
5. This is done by clicking on “New password” beside the user account and entering the
   desired password.
6. The integration with Wazuh is possible with the aid of TheHive REST API.
7. Therefore, we need a user on TheHive that can create alerts via the API.
8. We create an account with an “analyst” privilege for this purpose.
9. we generate the API key for the user:
10. In order to extract the API key, we reveal the key to view and copy it out for future use:

# Conﬁgure Wazuh manager:

1. Install TheHive Python module:

                  sudo /var/ossec/framework/python/bin/pip3 install thehive4py==1.8.1

2. Create the custom integration script by pasting the following python code in
   /var/ossec/integrations/custom-w2thive.py.
3. The lvl_threshold variable in the script indicates the minimum alert level that will be
   forwarded to TheHive.
4. The variable can be customized so that only relevant alerts are forwarded to TheHive.
5. Custom-w2thive.py:

                      #!/bin/sh
                      #Copyright (C) 2015-2020, Wazuh Inc.
                      #Created by Wazuh, Inc. <info@wazuh.com>.
                      #This program is free software; you can redistribute it and/or modify it under the terms of
                       GP>
                      WPYTHON_BIN="framework/python/bin/python3"
                      SCRIPT_PATH_NAME="$0"
                      DIR_NAME="$(cd $(dirname ${SCRIPT_PATH_NAME}); pwd -P)"
                      SCRIPT_NAME="$(basename ${SCRIPT_PATH_NAME})"
                      case ${DIR_NAME} in
                        */active-response/bin | */wodles*)
                         if [ -z "${WAZUH_PATH}" ]; then
                            WAZUH_PATH="$(cd ${DIR_NAME}/../..; pwd)"
                      if
                      PYTHON_SCRIPT="${DIR_NAME}/${SCRIPT_NAME}.py"
                      ;;
                      */bin)
                      if [ -z "${WAZUH_PATH}" ]; then
                        WAZUH_PATH="$(cd ${DIR_NAME}/..; pwd)"
                      if
                      PYTHON_SCRIPT="${WAZUH_PATH}/framework/scripts/${SCRIPT_NAME}.py"
                      ;;
                      */integrations)
                       if [ -z "${WAZUH_PATH}" ]; then
                        WAZUH_PATH="$(cd ${DIR_NAME}/..; pwd)" 
                      if
                      PYTHON_SCRIPT="${DIR_NAME}/${SCRIPT_NAME}.py"
                      ;;
                      esac
                      ${WAZUH_PATH}/${WPYTHON_BIN} ${PYTHON_SCRIPT} $@

 6. Change the ﬁles’ permission and the ownership to ensure that Wazuh has adequate
    permissions to access and run them:

                       sudo chmod 755 /var/ossec/integrations/custom-w2thive.py
                       sudo chmod 755 /var/ossec/integrations/custom-w2thive
                       sudo chown root:ossec /var/ossec/integrations/custom-w2thive.py
                       sudo chown root:ossec /var/ossec/integrations/custom-w2thive


 7. Allow Wazuh to run the integration script, Add the following lines to the manager
    conﬁguration ﬁle located at /var/ossec/etc/ossec.conf.
 8. Insert the IP address for TheHive server along with the API key that was generated earlier:

      # <ossec_config>
      ...

               <integration>
               <name>custom-w2thive</name>
               <hook_url>http://TheHive_Server_IP:9000</hook_url>
               <api_key>RWw/Ii0yE6l+Nnd3nv3o3Uz+5UuHQYTM</api_key>
               <alert_format>json</alert_format>
               </integration>

      ...
      # <ossec_config>

 9. Restart the manager to apply the changes:

               sudo systemctl restart wazuh-manager

 10. Log into TheHive with our test user account, and we can see Wazuh generated alerts
       under the “Alerts” tab:

 11. At this point, we can proceed to perform other standard TheHive actions on the alerts,
       such as creating cases on them or adding them to other existing cases.   

# Conclusion:

     - Wazuh is a ﬂexible security solution that integrates well with other solutions. It is open
       source and gives users the freedom to create and use custom integration scripts. This
       blog post shows that Wazuh integrates well with TheHive with the aid of custom scripts.
   
