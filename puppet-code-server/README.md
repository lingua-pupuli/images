# Puppet cdr/code-server

A self-contained Puppet developer experience inside a docker container.

This container image contains:

* Coder.com's [code-server](https://github.com/cdr/code-server)
* [Puppet Development Kit](https://github.com/puppetlabs/pdk)
* The [Puppet Extension for VSCode](https://github.com/lingua-pupuli/puppet-vscode) which works with code-server

## Go go gadget!

1. `docker pull lingua-pupuli/powershell-code-server`
2. `docker run -t -p 127.0.0.1:8443:8443 -v "${PWD}:/root/project" lingua-pupuli/powershell-code-server:stable code-server --allow-http --no-auth`
3. Open `http://localhost:8443` in your browser of choice
