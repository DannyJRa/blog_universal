---
title: Key Vault
author: DannyJRa
date: '2020-08-09'
categories:
  - Cloud
tags:
  - Azure
hidden: false
banner: "img/banners/hasicorp_vault_BLOG.png"
share: false
output:
  html_document:
    keep_md: yes
    theme: cerulean
    highlight: tango
    code_folding: show
    toc: yes
    toc_float: yes
  pdf_document:
    number_sections: yes
geometry: margin = 1.2in
fontsize: 10pt
always_allow_html: yes

---




ML Workspace ...
 
<!--more-->




Source: 
https://learn.hashicorp.com/tutorials/vault/getting-started-install?in=vault/getting-started

curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt-get update && sudo apt-get install vault

sudo apt  install jq

vault -autocomplete-install
# Usage

vault
vault server -dev

export VAULT_ADDR='http://127.0.0.1:8200'

export VAULT_TOKEN=<token>


vault kv put secret/hello foo=world

vault kv get secret/hello

vault kv put secret/hello foo=world excited=yes

vault kv get -field=excited secret/hello
vault kv get -format=json secret/hello | jq -r .data.data.excited

vault secrets list


# Starting server

vault server -config=/home/danny/vault/config.hcl


vault operator init -address=http://127.0.0.1:8200

export VAULT_ADDR='http://127.0.0.1:8200'

vault operator unseal

vault login <token>


vault kv get kv/test
vault kv get -format=json kv/test | jq -r .data.data.test_key

#Python
https://github.com/peopledoc/vault-cli
pip install vault-cli

