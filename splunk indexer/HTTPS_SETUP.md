2. Configuring Secure Connections (HTTPS / SSL)

To protect web traffic (port 8000) and REST API communications (port 8089) from interception, enable SSL/TLS encryption.

    Navigate to Settings -> Server settings -> General settings.

    Under the Splunk Web section, toggle Enable SSL (HTTPS) to Yes.

    If using custom SSL certificates, specify the PEM file paths in web.conf and server.conf.

    Restart Splunk web services to apply the new settings.
