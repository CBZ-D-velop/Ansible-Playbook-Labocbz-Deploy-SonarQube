# Ansible playbook: labocbz.deploy_sonarqube

![Licence Status](https://img.shields.io/badge/licence-MIT-brightgreen)
![CI Status](https://img.shields.io/badge/CI-success-brightgreen)
![Testing Method](https://img.shields.io/badge/Testing%20Method-Ansible%20Molecule-blueviolet)
![Testing Driver](https://img.shields.io/badge/Testing%20Driver-docker-blueviolet)
![Language Status](https://img.shields.io/badge/language-Ansible-red)
![Compagny](https://img.shields.io/badge/Compagny-Labo--CBZ-blue)
![Author](https://img.shields.io/badge/Author-Lord%20Robin%20Crombez-blue)

## Description

![Tag: Ansible](https://img.shields.io/badge/Tech-Ansible-orange)
![Tag: Debian](https://img.shields.io/badge/Tech-Debian-orange)
![Tag: Apache2](https://img.shields.io/badge/Tech-Apache2-orange)
![Tag: SSL/TLS](https://img.shields.io/badge/Tech-SSL%2FTLS-orange)
![Tag: SonarQube](https://img.shields.io/badge/Tech-SonarQube-orange)
![Tag: PostgreSQL](https://img.shields.io/badge/Tech-PostgreSQL-orange)
![Tag: Docker](https://img.shields.io/badge/Tech-Docker-orange)


An Ansible playbook to deploy and configure a SonarQube server on your hosts.

This Ansible playbook orchestrates the seamless deployment of SonarQube along with Apache2 as a reverse proxy, ensuring optimal performance and security for your development environment. SonarQube, a powerful code quality and security analysis tool, is deployed alongside PostgreSQL, managed through Docker containers, to provide a robust and scalable database backend.

Notably, SonarQube lacks native SSL support, making the presence of an SSL reverse proxy highly recommended for secure communication. Although SSL installation is not mandatory in this playbook, it is strongly encouraged to enhance the overall security posture of the deployment.

The playbook utilizes Docker to deploy SonarQube and PostgreSQL, eliminating the need for manual installation and ensuring consistency across environments. Apache2 installation, serving as the reverse proxy, is included to facilitate secure communication and efficient routing of incoming requests.

With Docker handling the deployment of SonarQube and PostgreSQL, the playbook streamlines the setup process, reducing complexity and ensuring reproducibility. By focusing on essential components and leveraging containerization technology, the playbook offers a straightforward and scalable solution for managing code quality and security analysis in your development environment.

With comprehensive security measures, including SSL configuration for Apache2, along with optimized performance settings, you can confidently deploy SonarQube and Apache2 while ensuring high availability, performance, and security for your applications.

## Deployment diagramm

![Ansible-Playbook-Labocbz-Install-SonarQube.drawio](./assets/Ansible-Playbook-Labocbz-Install-SonarQube.drawio.svg)

In this potential deployment scenario orchestrated by the playbook, we envision a robust architecture comprising Apache2, SonarQube, PostgreSQL, and Elasticsearch. Clients interact with SonarQube through Apache2, which serves as the SSL/TLS proxy, ensuring secure communication channels for accessing SonarQube functionalities and analysis results.

Within the deployment, SonarQube establishes communication with Elasticsearch and PostgreSQL, both residing on the same machine. Elasticsearch is seamlessly integrated into the SonarQube binaries, enhancing the search and analysis capabilities of the platform. The installation and configuration of PostgreSQL are efficiently handled by the SonarQube installation role, ensuring a basic yet functional setup for database management.

This deployment architecture not only facilitates secure and efficient access to SonarQube but also ensures seamless integration with Elasticsearch and PostgreSQL. By leveraging Apache2 as the SSL/TLS proxy and incorporating Elasticsearch within the SonarQube environment, the playbook offers a comprehensive solution for managing code quality and security analysis in your development environment.

## Tests and simulations

### Basics

You have to run multiples tests. *tests with an # are mandatory*

```MARKDOWN
# lint
# syntax
# converge
# idempotence
# verify
side_effect
```

Executing theses test in this order is called a "scenario" and Molecule can handle them.

Molecule use Ansible and pre configured playbook to create containers, prepare them, converge (run the playbook) and verify its execution.
You can manage multiples scenario with multiples tests in order to get a 100% code coverage.

This playbook contains a ./tests folder. In this folder you can use the inventory or the tower folder to create a simualtion of a real inventory and a real AWX / Tower job execution.

### Command reminder

```SHELL
# Check your YAML syntax
yamllint -c ./.yamllint .

# Check your Ansible syntax and code security
ansible-lint --config=./.ansible-lint .

# Execute and test your playbook
molecule lint
molecule create
molecule list
molecule converge
molecule verify
molecule destroy

# Execute all previous task in one single command
molecule test
```

## Installation

To install this playbook, just copy/import this playbook or raw file into your fresh playbook repository or call it with the "include_playbook/import_playbook" module.

## Usage

### Vars

```YAML
# From inventory
---
# all vars from to put/from your inventory
# see tests/inventory/group_var for all groups and vars.
```

```YAML
# From AWX / Tower
---
all vars from to put/from AWX / Tower
```

## Architectural Decisions Records

Here you can put your change to keep a trace of your work and decisions.

### 2024-01-03: First Init

* First init of this playbook with the bootstrap_playbook playbook by Lord Robin Crombez
* Playbook deploy PostgreSQL, Apache2 and SonarQube
* You can install or not Apache2
* Tests added and validated with a local project to analyse
* Pay attention of self signed certs !

### 2024-03-02: Fix and CI

* Added support for new CI base
* Edit all vars with __
* Tested and validated on Docker

## Authors

* Lord Robin Crombez

## Sources

* [Ansible playbook documentation](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_playbooks.html)
* [Ansible Molecule documentation](https://molecule.readthedocs.io/)
* [labocbz.prepare_host](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Prepare-Host.git)
* [labocbz.add_certificates](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Add-Certificates.git)
* [labocbz.install_sonarqube](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-SonarQube.git)
* [labocbz.install_apache](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Apache.git)
* [labocbz.add_apache_confs](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Add-Apache-Confs.git)
* [labocbz.add_logrotate_confs](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Add-Logrotate-Confs.git)
* [labocbz.install_java](https://github.com/CBZ-D-velop/Ansible-Role-Labocbz-Install-Java.git)
