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
    ```
    cd docker
    sudo docker build -tag=dockertesttag .
    sudo docker run -d --name docker_test -p4000:80 dockertesttag
    ```
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
    * You can also run the following command _(Note: The following command can be run from another directory too. Just make sure the path to the checks file is modified.)_
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
5. Docker Connector
    * Run the following command from `independent.study/testing/`
        ```
            opunit verify docker_test
        ```

## Testing your local machine using a profile
1. Use can use a [profile](https://github.com/CSC-DevOps/profile) to test your local machine
    ```
        opunit profile CSC-DevOps/profile:519.yml
    ```
