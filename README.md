# Local Development Environment for WordPress using Vagrant

This repository contains a Vagrantfile and a WordPress configuration file for setting up a local development environment for WordPress.

## Requirements

- Vagrant
- VirtualBox

## Installation

- Clone this repository to your local machine.
- Install Vagrant and VirtualBox.
- Open a terminal or command prompt and navigate to the cloned repository directory.
- Run the following command to start the virtual machine:

        vagrant up

- Once the virtual machine has been started, open a web browser and navigate to `http://[YOUR_IP_ADDRESS]/wp-admin` to access your local WordPress installation.

## Configuration

This Vagrantfile uses the `geerlingguy/ubuntu2004` box and sets up the following software on the virtual machine:

- Apache2
- MySQL server
- PHP
- php-bcmath
- php-curl
- php-imagick
- php-intl
- php-json
- php-mbstring
- php-mysql
- php-xml
- php-zip

The virtual machine is also configured with a private network IP address - check your network and use address within your ranges - and port 80 is forwarded from the guest to the host machine.

## Usage

To start the virtual machine, navigate to the directory containing the Vagrantfile in your terminal or command prompt and run:

    vagrant up

To access the virtual machine, run:

    vagrant ssh

To stop the virtual machine, run:

    vagrant halt

## Contributing

Contributions to this repository are welcome. If you encounter any issues or have suggestions for improvements, please submit an issue or pull request.
License

This project is licensed under the MIT License.
