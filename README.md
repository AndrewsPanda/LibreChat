# Changes I have made to the standard configuration of LibreChat

## I am already self hosting Nginx as a Reserve Proxy
# Remove Port Mapping for NGINX in deploy-compose.yml

* Update the LibreChat-NGINX service in deploy-compose.yml to avoid port conflicts:

client:
  image: nginx:1.27.0-alpine
  container_name: LibreChat-NGINX
  depends_on:
    - api
  restart: always
  volumes:
    - ./client/nginx.conf:/etc/nginx/conf.d/default.conf

* I removed the following from the above section:

    ports:
      - 80:80
      - 443:443

* Restart Nginx and Docker Services:

sudo systemctl reload nginx
sudo docker-compose -f ./deploy-compose.yml down
sudo docker-compose -f ./deploy-compose.yml up -d


## .env changes 

### DISABLE_COMPRESSION=true

I activated 'DISABLE_COMPRESSION=true' in .env

* Reason, I already have 'gzip on;' enabled for compression in my '/etc/nginx/nginx.conf' file.

### UID/GID

In your .env file, the UID and GID variables are commented out:

* UID=1000
* GID=1000

To resolve these warnings, you can uncomment these lines and set the appropriate user ID and group ID.

Run the fulling command to get the variables

* id -u  # For UID
* id -g  # For GID