Vault comes with various pluggable components called secrets engines and authentication methods allowing you to integrate with external systems. The purpose of those components is to manage and protect your secrets in dynamic infrastructure (e.g. database credentials, passwords, API keys).

Vault operates as a client-server application. The Vault server is the only piece of the Vault architecture that interacts with the data storage and backends. All operations done via the Vault CLI interact with the server over a TLS connection.



https://developer.hashicorp.com/vault/tutorials/getting-started/getting-started-dev-server



HashiCorp officially maintains and signs packages for the following Linux distributions.

Amazon Linux
Install yum-config-manager to manage your repositories.

 sudo yum install -y yum-utils

Use yum-config-manager to add the official HashiCorp Linux repository.

 sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo

Install.

 sudo yum -y install vault


 
[ec2-user@ip-172-31-29-0 ~]$ vault version
Vault v1.14.0 (13a649f860186dffe3f3a4459814d87191efc321), built 2023-06-19T11:40:23Z


vault server -dev

WARNING! dev mode is enabled! In this mode, Vault runs entirely in-memory
and starts unsealed with a single unseal key. The root token is already
authenticated to the CLI, so you can immediately begin using Vault.

You may need to set the following environment variables:

    $ export VAULT_ADDR='http://127.0.0.1:8200'

The unseal key and root token are displayed below in case you want to
seal/unseal the Vault or re-authenticate.

Unseal Key: PGyR5UqQ8bkcVX3XssaXH0u3ZtNG/6D+cfpqyAVPiJs=
Root Token: hvs.aGT623WhZTwgiitFuwo2XwZN



