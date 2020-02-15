# home-playbook

Playbooks for installing [AWX](https://github.com/ansible/awx) and [netbox-docker](https://github.com/netbox-community/netbox-docker) on a Manjaro Linux server

## Files

* `awx-playbook.yml`
  * Playbook for installing AWX
* `netbox-playbook.yml`
  * Playbook for installing Netbox
* `manjaro-playbook.yml`
  * Playbook for updating/installing packages for Manjaro Linux
* `site.yml`
  * Run all playbooks

## How to use

1. Prepare a Manjaro Linux server
    * `openssh` and `python` packages must be installed
2. Install [Ansible](https://github.com/ansible/ansible) on local PC
3. Clone this repo
4. Create Ansible inventory file
    ```ini
    [awx_hosts]
    manjaro1 ansible_host=192.168.0.1

    [awx_hosts:vars]
    awx_version="9.2.0"

    [netbox_hosts]
    manjaro1 ansible_host=192.168.0.1

    [netbox_hosts:vars]
    netbox_version="v2.7"
    netbox_nginx_port=8080

    [manjaro_hosts]
    manjaro1 ansible_host=192.168.0.1
    ```
5. Run `site.yml`
    ```console
    $ ansible-playbook -i inventory site.yml -k -K
    ```

Once above steps are completed, AWX and netbox-docker are prepared on the Manjaro Linux server.

* AWX
  * http://192.168.0.1/
* netbox-docker
  * http://192.168.0.1:8080/
