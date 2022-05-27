FROM ghcr.io/inmanta/orchestrator:dev

# We need to become root for the next operations
USER root

# Install code-server in the container image
RUN cd /opt && \
    git clone https://github.com/coder/code-server.git && \
    chown -R inmanta:inmanta code-server && \
    cd code-server && \
    chmod +x install.sh && \
    ./install.sh

# Install the python extension
RUN sudo -u inmanta code-server --install-extension ms-python.python

# Install the inmanta extesion (to be fixed)
RUN mkdir -p /var/lib/inmanta/.local/share/code-server/extensions && \
    cd /var/lib/inmanta/.local/share/code-server/extensions && \
    git clone https://github.com/inmanta/vscode-inmanta.git inmanta.inmanta-dev && \
    chown -R inmanta:inmanta /var/lib/inmanta

# Copy the startup confguration where code-server will pick it up
COPY ./resources/code-server-config.yml /var/lib/inmanta/.config/code-server/config.yaml

# Setting the user back to what is was
USER inmanta

# Overwrite the entrypoint to first start the code server, then use the entrypoint from
# the base container image
ENTRYPOINT ["/usr/bin/bash", "-c", "sudo -u inmanta code-server & /container-entrypoint-with-env $@", ""]
