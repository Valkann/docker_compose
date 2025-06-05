# Vaultwarden Docker Compose

## Note

- You need a reverse proxy configuration to access your password manager from the outside.

## Create Folders
- [ROOT_FOLDER]/data

## Code 

```
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: always
    environment:
      DOMAIN: "[EXTERNAL URL]" # required when using a reverse proxy; your domain; vaultwarden needs to know it's https to work properly with attachments
      SIGNUPS_ALLOWED: "false" # Deactivate this with "false" after you have created your account so that no strangers can register
    volumes:
      - [ROOT_FOLDER]/data:/data # the path before the : can be changed
    ports:
      - [NAS PORT]:80 # you can replace the [NAS PORT] with your preferred port
```

## File
- [compose.yaml](./compose.yaml)