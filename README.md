# Docker-LAMP
A LAMP fullstack with latest release of 8.1 and Composer, MySQL, Apache, PHPMyAdmin

## Usage
1. Clone this repository
2. Run `docker-compose up -d`
3. Go to `http://localhost` to see the **`phpinfo`** page
4. Go to `http://localhost:8080` to see the PHPMyAdmin page

## Configuration
PHP Version
- Default is set to `8.1`
You can change it in the [Dockerfile](.docker/php/Dockerfile):
```dockerfile
# Base image
FROM ubuntu:latest

ENV php_version=8.1
...
```
