# Testing connectors and checks after refactoring

## Setup

1. Setup Vagrant Machine
    ```
    cd vagrant
    vagrant up
    ```
2. Setup Baker Machine
    ```
    cd baker
    baker bake
    ```
3. Setup Docker
4. Setup Slim

## Testing using Inventory file

1. Make sure that you are currently in the directory `independent.study/testing`
2. Run the command:
    ```
    opunit verify -i inventory.yml
    ```

## Testing Individual Connectors

1. SSHConnector
    * Run the following command from `independent.study/testing/vagrant`
        ```
            opunit verify vagrant@192.168.33.100 --ssh_key .vagrant/machines/vagrant_test/virtualbox/private_key -c ../test/opunit.yml
        ```
2. Vagrant Connector
    * Run the following command from `independent.study/testing/vagrant`
        ```
            opunit verify -c ../test/opunit.yml
        ```
    * You can also run the following command
        ```
            opunit verify vagrant_test -c ../test/opunit.yml
        ```
3. Baker Connector
    * Run the following command from `independent.study/testing/baker`
        ```
            opunit verify -c ../test/opunit.yml
        ```
4. Local Connector
    * Run the following command from `independent.study/testing/`
        ```
            opunit verify local
        ```
5. 

