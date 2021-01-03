# Reload nginx configuration

To take effect of changes in the nginx configuration, i know that i have to restart then nginx service.
Today i learned, that it is not the best way, because nginx has to shutdown and completly restart the service. 
The problem is, that it take long because nginx waits to close all connections.

The better way is to `reload` the configuration instead of `restart` the nginx service.
```bash
service nginx reload
```