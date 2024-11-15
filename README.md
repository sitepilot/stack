# Stack

Effortlessly provision high-performance Linux Containers (LXC), fine-tuned for WordPress and Laravel.

## About

[Sitepilot](https://sitepilot.io) utilizes LXD-managed hosts and orchestrated LXC software containers for each site. 
This means that every site is housed in its own isolated container, complete with all the software resources required 
to run it. The resources are 100% private and are not shared with anyone else.

We've open-sourced these Ansible playbooks so you can see exactly how our containers and hosts are configured, or even 
use them yourself to host sites. This gives you full transparency into our setup and the flexibility to adapt it to your 
own hosting environment.

## Software

### Server

Below is a list of the software that will be installed on a LXD-managed host.

* **[Nginx](roles/server/nginx/defaults/main.yml)** - Nginx is installed to forward (proxy) web and SSH traffic to the correct container.

### Container

Below is a list of the software that can be installed in a container. Only the necessary software is included, 
ensuring a lightweight and efficient environment tailored specifically to run the site.

* **[PHP](roles/container/php/defaults/main.yml)** - Installed when `php_version` is specified.
* **[Composer](roles/container/composer/defaults/main.yml)** - Installed when `php_version` is specified.
* **[WPCLI](roles/container/wpcli/defaults/main.yml)** - Installed when `php_version` is specified.
* **[Node.js](roles/container/node/defaults/main.yml)** - Installed when `node_version` is specified.
* **[Nginx](roles/container/nginx/defaults/main.yml)** - Installed when `server_type` is set to `nginx`.
* **[MariaDB](roles/container/mariadb/defaults/main.yml)** - Installed when `database_type` is set to `mariadb`.
* **[Valkey](roles/container/valkey/defaults/main.yml)** - Installed when `cache_type` is set to `valkey`.
* **[WordPress](roles/container/wordpress/defaults/main.yml)** - Installed when `container_type` is set to `wordpress`.

If software does not need to be installed, it will be automatically removed from the container.

## Security Vulnerabilities

Please don't disclose security-related issues publicly. If you discover a security vulnerability within Laravel, 
please send an email to support at support@sitepilot.io. All security vulnerabilities will be promptly addressed.
