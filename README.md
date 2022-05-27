# Inmanta with vscode

This simple project quickly sets up an development environment for working on inmanta models.  It starts two containers: an postgresql db for the inmanta server, and an inmanta server along which is installed a vscode server, the latter can be used to easily edit the model you are deploying with the orchestrator.

## How to use

### Start the containers
```bash
docker-compose up
```

### Access the orchestrator
Simply open a navigator to the following url: [http://172.30.0.3:8888](http://172.30.0.3:8888).

### Access the vscode environment
You can then access the web interface at [http://172.30.0.3:8080](http://172.30.0.3:8080).
