# Inmanta with vscode

This simple project quickly sets up an development environment for working on inmanta models.  It starts three containers: an postgresql db for the inmanta server, an inmanta server and a vscode server, which can be used to easily edit the model you are deploying with the orchestrator.

## How to use

### Create the data shared folder
```bash
# Create the folder
mkdir data

# Give ownership to the inmanta user (inside of the container)
sudo chmod 997:995 data -R
```

### Start the containers
```bash
docker-compose up
```

### Access the orchestrator
Simply open a navigator to the following url: [http://172.30.0.3:8888](http://172.30.0.3:8888)

### Access the vscode environment
```console
$ docker exec vscode cat .config/code-server/config.yaml
bind-addr: 127.0.0.1:8080
auth: password
password: e8335e22529fdb0b78a54b07
cert: false
```

You can then access the web interface at [http://172.30.0.4:8080](http://172.30.0.4:8080) and authenticate using the password you have found in your running container.
