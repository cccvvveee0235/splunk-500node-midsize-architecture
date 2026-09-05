Splunk Indexer Configuration Guide

This document provides a step-by-step guide for the initial setup of a Splunk Indexer node: creating custom user accounts, enabling HTTPS, configuring data receiving ports, and managing index storage paths.

1. Creating Custom Accounts and Roles

Using the default admin account for daily operations is unsafe. Set up dedicated user accounts with restricted privileges based on necessary roles. For example, I created my own account and assigned a special role to it.

    In the Splunk Web interface, navigate to Settings -> Users (or Roles).

    Click New User, then enter the username and password.

    Assign appropriate roles (e.g., power, data_management_admin or a custom administrator role).

    Save the changes and verify login using the new account.
**1. Create User and Roles**

<img src="assets/Splunk roles.png" alt="Creating Users and Roles" >

<img src="assets/Splunk roles2.png" alt="Creating Users and Roles" >

<img src="assets/Splunk roles3.png" alt="Creating Users and Roles" >

<img src="assets/Splunk roles4.png" alt="Creating Users and Roles" >

2. Configuring Secure Connections (HTTPS / SSL)

To protect web traffic (port 8000) and REST API communications (port 8089) from interception, enable SSL/TLS encryption.

    Navigate to Settings -> Server settings -> General settings.

    Under the Splunk Web section, toggle Enable SSL (HTTPS) to Yes.

    If using custom SSL certificates, specify the PEM file paths in web.conf and server.conf.

    Restart Splunk web services to apply the new settings.
