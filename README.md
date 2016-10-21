MesosLocal
==========

MesosLocal creates a local Mesos environment for development using Docker Compose. It is compatible with [Docker For Mac](https://docs.docker.com/docker-for-mac/) and [Docker For Windows](https://docs.docker.com/docker-for-windows/). MesosLocal makes it easier to develop against Mesos in a local environment.

Included Services:
  - Zookeeper
  - Mesos
  - Marathon Framework
  - Chronos Framework


Getting Started
---------------

Install Docker and Docker Compose, or install Docker For Mac/Windows (which includes Docker Compose).

To launch, run:

    $ docker-compose up

This may take a few minutes while the required Docker images are downloaded. **NOTE:** docker-compose will run in the foreground and print logs from the launched services, append the flag `-d` to run in the background.

Once launched, the Mesos, Marathon and Chronos dashboards should be available:

  - [Mesos Dashboard](http://127.0.0.1:5050)
  - [Marathon Dashboard](http://127.0.0.1:8080)
  - [Chronos Dashboard](http://127.0.0.1:4400)

To view the running services statuses, run:

    $ docker-compose ps

To view the running services logs, run:

    $ docker-compose logs [optional services name to filter]

To stop the services, press `CTRL-C` in the docker-compose log tailer, or if running in the background run:

    $ docker-compose stop

To destroy all saved state of a previous invocation, run:

    $ docker-compose rm


Troubleshooting
---------------

### I get an error when accessing a Mesos sandbox

The Mesos dashboard communicates with Mesos slaves using hostnames, however Docker Compose does not export the hostnames used internally to the host, only the exposed ports.

Using either the hosts file or your local DNS server, set up the following hosts:

    127.0.0.1 zookeeper mesos-master mesos-server marathon chronos

