# n8n Docker Compose

## Note
Values in [] are the values you need to replace with your own information.

## Create Folders
- [ROOT_FOLDER]/n8n
- [ROOT_FOLDER]/n8n/local-files

## Permisions
Be sure that the `node` user is OWNER of the Folder. 

`sudo chown -R 1000:1000 [ROOT_FOLDER] /n8n/`


## Code

```
services:
  n8n:
    image: docker.n8n.io/n8nio/n8n:latest
    container_name: n8n-automation-platform
    restart: always
    ports:
      - "0.0.0.0:[NAS PORT]:5678"
    environment:
      - N8N_HOST=0.0.0.0
      - N8N_PORT=5678
      - N8N_PROTOCOL=https
      - NODE_ENV=production
      - WEBHOOK_URL=[EXTERNAL URL]
      - N8N_EDITOR_BASE_URL=[EXTERNAL URL]
      - N8N_RUNNERS_ENABLED=false
      - GENERIC_TIMEZONE=[TIMEZONE example: Europe/Paris]
      - N8N_SECURE_COOKIE=false
    volumes:
      - [ROOT_FOLDER]/n8n:/home/node/.n8n
      - [ROOT_FOLDER]/n8n/local-files:/files
```
## File
- [compose.yaml](./compose.yaml)