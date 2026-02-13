# Monitoring Stack with Infrastructure as Code

Automated deployment of a Grafana + Prometheus monitoring stack using Infrastructure as Code. <br>
This repository provisions a complete monitoring environment inside a Virtual Machine using Vagrant and Ansible.


## How It Works

When `vagrant up` is executed:

* Vagrant creates an Ubuntu VM using VirtualBox
* Ansible runs automatically as the provisioner
* Prometheus, Node Exporter, and Grafana are installed and configured
* Prometheus scrapes metrics from Node Exporter
* Grafana connects to Prometheus as a data source

Everything is provisioned automatically. No manual setup inside the VM is required.

> This project was built for study purposes and demonstrates infrastructure automation, reproducibility, and environment standardization using IaC principles.

## Prerequisites

Make sure you have installed:

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](https://developer.hashicorp.com/vagrant/install#darwin)
* [Git](https://git-scm.com/install/windows)

You can verify with:

```
vagrant --version
git --version
```


## Getting Started

### 1. Clone the repository

```
git clone https://github.com/devbeatriz/iac-monitoring-lab.git
```

### 2. Enter the project folder

After cloning, a folder named `iac-monitoring-lab` will be created:

```
cd iac-monitoring-lab
```

Run the next command inside this folder, where the `Vagrantfile` is located.

### 3. Start the VM

```
vagrant up
```

Wait until Ansible finishes provisioning.


## Access
The VM uses a fixed private IP address: 192.168.56.20

### 1. Access the VM via SSH (optional)

```
 vagrant ssh
```

### 2. Open in your browser

Grafana

```
http://192.168.56.20:3000
```

Prometheus

```
http://192.168.56.20:9090
```

### Default Grafana Credentials

User: `admin`
Password: `admin`

You will be prompted to change the password on first login.

## Project Structure

```
iac-monitoring-lab/
│
├── Vagrantfile
├── inventory
├── playbook.yml
│
├── roles/
│   ├── prometheus/
│   ├── grafana/
│   └── node_exporter/
│
└── README.md
```

The `Vagrantfile` starts the VM and triggers Ansible.
The playbook orchestrates the roles responsible for installing and configuring each service.


## What I Learned

Through this project, I practiced:

* Infrastructure as Code concepts
* Automating provisioning with Ansible
* Structuring Ansible roles in a modular way
* Configuring Prometheus to collect metrics
* Integrating Grafana with Prometheus
* Creating reproducible environments

This hands-on lab helped me better understand how a monitoring stack is structured and automated in practice.

