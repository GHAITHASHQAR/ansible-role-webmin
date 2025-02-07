# Ansible Role: Webmin

This Ansible role automates the installation and configuration of **Webmin** on Ubuntu systems. It includes the installation of dependencies, repository configuration, Webmin setup, and configuration options.

## Requirements

- Ansible 2.9+
- Supported OS:
  - Ubuntu 18.04, 20.04, or later

## Role Variables

| Variable                       | Default Value          | Description |
|--------------------------------|------------------------|-------------|
| `webmin_port`                 | `10000`               | Port on which Webmin will be accessible. |
| `webmin_listen`               | `0.0.0.0`             | IP address Webmin listens on. |
| `webmin_ssl`                  | `1`                   | Enable or disable SSL (1 = enabled, 0 = disabled). |
| `webmin_reverse_proxy_referer`| Not defined           | A comma-separated list of reverse proxy referers. |

## Tasks Overview

### Dependencies Installation
The role installs essential packages required for Webmin to function properly, including Perl, SSL libraries, and PAM authentication modules.

### Repository Configuration
The Webmin repository is added and the GPG key is installed to authenticate packages.

### Webmin Installation
The Webmin package is installed from the repository and configured based on user-defined variables.

### Configuration Customization
The following configurations are applied to `/etc/webmin/miniserv.conf`:
- **Port**: The port Webmin will listen on.
- **Listen Address**: The IP address Webmin listens on.
- **SSL**: Whether SSL is enabled or disabled.
- **Reverse Proxy Referer**: Optionally set a referer for reverse proxying.

### Service Verification
The role ensures Webmin is started and waits for the configured port to become accessible.

## Handlers
- `restart webmin`: Restarts the Webmin service after configuration changes.


## Tags

| Tag          | Purpose |
|--------------|---------|
| `dependencies` | Installs required dependencies for Webmin. |
| `webmin`      | Installs and configures Webmin. |

## License

MIT

## Author

Maintained by [AIT-CS IaaS](https://github.com/ait-cs-IaaS).
