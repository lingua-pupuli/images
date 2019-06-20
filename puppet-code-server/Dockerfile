FROM codercom/code-server:latest

ARG PUPPET_EXTENSION_VERSION=0.18.0

ADD https://apt.puppetlabs.com/puppet6-release-xenial.deb /tmp/puppet6-release-xenial.deb
RUN sudo dpkg -i /tmp/puppet6-release-xenial.deb

RUN echo "" \
    && sudo apt-get update \
    && sudo apt-get install -y \
        pdk \
        ca-certificates \
        gss-ntlmssp \
    && sudo apt-get dist-upgrade -y \
    && sudo apt-get clean \
    && sudo rm -rf /var/lib/apt/lists/* \
    && sudo rm /tmp/puppet6-release-xenial.deb

RUN mkdir -p ~/.local/share/code-server/extensions/
COPY jpogran.puppet-vscode-0.18.0/ /home/coder/.local/share/code-server/extensions/jpogran.puppet-vscode-0.18.0
RUN ls -la ~/.local/share/code-server/extensions/

ARG IMAGE_NAME=jpogran/puppet-code-server:latest

LABEL maintainer="James Pogran <ender@puppet.com>" \
      readme.md="https://github.com/jpogran/puppet-code-server/blob/master/README.md" \
      description="Coder.com's code-server, Puppet, and the Puppet extension for VScode - all in one container." \
      org.label-schema.url="https://github.com/jpogran/puppet-code-server" \
      org.label-schema.vcs-url="https://github.com/jpogran/puppet-code-server" \
      org.label-schema.name="jpogran" \
      org.label-schema.vendor="jpogran" \
      org.label-schema.version=${PUPPET_EXTENSION_VERSION} \
      org.label-schema.schema-version="1.0" \
      org.label-schema.vcs-ref=${VCS_REF} \
      org.label-schema.docker.cmd="docker run -t -p 127.0.0.1:8443:8443 -v '\${PWD}:/root/project' ${IMAGE_NAME} code-server --allow-http --no-auth"
