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

## License

Copyright 2022 Guillaume Everarts de Velp

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
