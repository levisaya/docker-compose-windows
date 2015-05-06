# -*- mode: ruby -*-
# vi: set ft=ruby :

# Specify Vagrant version and Vagrant API version
Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Configure the Docker provider for Vagrant
  config.vm.provider "docker" do |docker|

    # Specify the Vagrantfile of the host VM.
    # Without this, the Vagrant will use a default boot2docker image.
    docker.vagrant_vagrantfile = "host/Vagrantfile"

    # Specify the Docker image to spin up.
    # This image simply installs Docker Compose so we can run it.
    # You can check out it out in more detail at https://registry.hub.docker.com/u/dduportal/docker-compose/.
    docker.image = "dduportal/docker-compose:latest"

    # Give the container a nice name.
    docker.name = "docker-compose-container"

    # Share some files/folders from the host VM to the Docker Compose container.
    # /app is the folder we mapped in our host VM that is the root of the project.
    # /var/run/docker.sock is the socket used by Docker.
    docker.volumes = ["/app:/app", "/var/run/docker.sock:/var/run/docker.sock"]

    # The command to run in the container. The Dockerfile for the docker-compose container
    # specifies /usr/local/bin/docker-compose as the entrypoint, so we can just call up to
    # start all our containers specified in docker-compose.yml.
    docker.cmd = ["up"]
  end
end