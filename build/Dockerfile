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

# Build and install the inmanta vscode extension
RUN cd /tmp && \
    git clone https://github.com/inmanta/vscode-inmanta.git && \
    chown -R inmanta:inmanta vscode-inmanta && \
    cd vscode-inmanta && \
    sudo -u inmanta npm i vsce && \
    sudo -u inmanta npx vsce package && \
    sudo -u inmanta code-server --install-extension inmanta-*.vsix && \
    cd /tmp && \
    rm -rf vscode-inmanta

# Copy the startup confguration where code-server will pick it up
COPY ./resources/code-server-config.yml /var/lib/inmanta/.config/code-server/config.yaml

# Copy the vscode settings file in place
COPY ./resources/code-server-settings.json /var/lib/inmanta/.local/share/code-server/User/settings.json

# Setting the user back to what is was
USER inmanta

# Overwrite the entrypoint to first start the code server, then use the entrypoint from
# the base container image
ENTRYPOINT ["/usr/bin/bash", "-c", "sudo -u inmanta code-server & /container-entrypoint-with-env $@", ""]
