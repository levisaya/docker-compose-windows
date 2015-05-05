# -*- mode: ruby -*-
# vi: set ft=ruby :

# Specify Vagrant version and Vagrant API version
Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

# Create and configure the Docker container(s)
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Configure the Docker provider for Vagrant
  config.vm.provider "docker" do |docker|

    # Define the location of the Vagrantfile for the host VM
    # Comment out this line to use default host VM that is
    # based on boot2docker
    docker.vagrant_vagrantfile = "host/Vagrantfile"

    # Specify the Docker image to use
    docker.image = "dduportal/docker-compose:latest"

    # Specify a friendly name for the Docker container
    docker.name = "docker-compose-container"

    docker.volumes = ["/app:/app", "/var/run/docker.sock:/var/run/docker.sock"]

    docker.cmd = ["up"]
  end
end