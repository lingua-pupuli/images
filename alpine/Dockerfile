FROM puppet/puppet-agent-alpine:latest

ARG LANG_SERVER_VERSION=0.16.0
ARG IMAGE_NAME=lingua-pupuli/languageserver:0.16.0

LABEL maintainer="Lingua-Pupuli Team" \
        readme.md="https://github.com/lingua-pupuli/images/blob/master/README.md" \
        description="This Dockerfile will install the latest release of the Puppet Language Server." \
        org.label-schema.usage="https://github.com/lingua-pupuli/images/blob/master/README.md#run-the-docker-image-you-built" \
        org.label-schema.url="https://github.com/lingua-pupuli/images/blob/master/README.md" \
        org.label-schema.vcs-url="https://github.com/lingua-pupuli/images" \
        org.label-schema.name="languageserver" \
        org.label-schema.vendor="lingua-pupuli" \
        org.label-schema.version=${LANG_SERVER_VERSION}} \
        org.label-schema.schema-version="1.0"

ADD "https://github.com/lingua-pupuli/puppet-editor-services/releases/download/${LANG_SERVER_VERSION}/puppet_editor_services_${LANG_SERVER_VERSION}.tar.gz" /puppet_editor_services_${LANG_SERVER_VERSION}.tar.gz

RUN mkdir /puppet_editor_services \
    && cd /puppet_editor_services \
    && tar -xzf /puppet_editor_services_${LANG_SERVER_VERSION}.tar.gz

EXPOSE 8082

ENTRYPOINT ["/usr/bin/ruby"]

CMD ["/puppet_editor_services/puppet-languageserver", "--ip=0.0.0.0", "--port=8082", "--timeout=0", "--debug=STDOUT", "--no-stop"]
