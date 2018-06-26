FROM puppet/puppet-agent-alpine

RUN apk add --update git \
    && git clone https://github.com/lingua-pupuli/puppet-editor-services.git

EXPOSE 8082

ENTRYPOINT ["/usr/bin/ruby"]

CMD ["/puppet-editor-services/puppet-languageserver", "--ip=0.0.0.0", "--port=8082", "--timeout=0", "--debug=STDOUT", "--no-stop"]
