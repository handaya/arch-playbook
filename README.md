# arch-playbook

Playbooks for installing [AWX](https://github.com/ansible/awx) and [netbox-docker](https://github.com/netbox-community/netbox-docker) on a Manjaro Linux server

## Files

* `manjaro-bootstrap.yml`
  * Playbook for installing AWX and netbox-docker on a Manjaro Linux server
* `manjaro-playbook.yml`
  * Playbook for installing some packages and updating system

## How to use

1. Prepare a Manjaro Linux server
    * `openssh` and `python` packages must be installed
2. Install [Ansible](https://github.com/ansible/ansible) on local PC
3. Clone this repo
4. Create `inventory` with `[manjaro_hosts]` group
    ```ini
    [manjaro_hosts]
    manjaro1 ansible_host=192.168.0.1
    ```
5. Run `manjaro-bootstrap.yml`
    ```console
    $ ansible-playbook -i inventory manjaro-bootstrap.yml -k -K
    ```

Once above steps are completed, AWX and netbox-docker are prepared on the Manjaro Linux server.

* AWX
  * http://192.168.0.1/
* netbox-docker
  * http://192.168.0.1:8080/

`manjaro-playbook.yml` can be run locally, but it should be run from AWX which is already prepared.
