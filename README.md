# CSC: 630

## Setup

1. Clone the repository
    ```
    git clone https://github.com/JerryD10/independent.study
    ```

## Testing docable issue # 16

## Before you get started

* Clone this repo with: `git clone https://github.com/CSC-DevOps/CM` 
* Make sure you have a shell open in the right directory: `cd CM`.
* Update opunit: `npm install opunit -g`. Ensure `opunit --version >= 0.4.4`.
* Update bakerx, take advantage of the new `--ip` option: `npm install ottomatica/bakerx -g` or `cd bakerx && npm install && npm update`. Ensure `bakerx --version` says `bakerx@0.6.7 virtcrud@1c9b4ba`.


## Creating your servers 

### The configuration server ⚒️

Create the Virtual Machine.

```bash
$ bakerx run ansible-srv bionic --ip 192.168.33.10
```
Inside the ansible-srv, install ansible:

```bash
sudo add-apt-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible -y
```

Verify that ansible was installed by running opunit.

```
$ opunit verify vagrant@192.168.33.10 --ssh_key ~/.bakerx/insecure_private_key -c test/ansible-srv.yml  
```

### The web server 🌐

Let's create another virtual machine for the web server. 

```bash
$ bakerx run web-srv bionic --ip 192.168.33.100
```

#### Completing workshop checks

You should be able to verify all checks pass:

    opunit verify -i opunit_inventory.yml

Great work!

## Cleaning Up
Clean all the files associated with the web server

```bash
$ rm -f web-srv web-srv.pub
```

Destroy the ansible-srv machine

```bash
$ bakerx delete vm ansible-srv
```

Destroy the web-srv machine

```bash
$ bakerx delete vm web-srv
```