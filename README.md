# Ansible Playbook for deploying the OpenBalena server

## Project setup

This playbook expects a Linux server that is reachable via a domain with open ports 22,80,443 and 3128.
The domain needs to be configured so that CNAME records for the following subdomains point to your server: api, registry, vpn, s3, tunnel

Specify your configuration details in the `inventory.yaml` file.
The `username` and `password` credentials will later be used to authenticate with your OpenBalena instance.

Additionally, you will need an SSH key file that allows connecting to your server.
You can also change the location of this file in the `inventory.yaml` file.

## Installing OpenBalena using Ansible

To install OpenBalena, you need to have Ansible installed.
After finishing the configuration, you can deploy your ansible playbook.

```bash
ansible-playbook -i inventory.yaml playbook.yaml
```

## Using OpenBalena

For information about using OpenBalena, have a look at their official documentation: https://open-balena-docs.balena.io/getting-started/

To connect to balena, you need to add the balena URL to your local balena configuration file `~/.balenarc.yml`:

```yaml
balenaUrl: 'your-domain-here.com'
```

Now you can use your balena CLI to log in with the credentials you have set in the `inventory.yaml` file.
This enables you to use the balena CLI as usual.

```bash
balena login
balena fleets
```