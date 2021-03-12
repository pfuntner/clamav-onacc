# clamav-onacc
Ansible playbooks to install and customize ClamAV and test against infected files.

## Supported Linux distros
* Debian 9
* Debian 10
* Ubuntu 16.04
* Ubuntu 18.04
* Ubuntu 20.04

### Qualified support
There is qualified support for other distros:
* ClamAV packages are not available on for every distro on every cloud provider.  For example:
  * RHEL 7, 8 on Amazon Web Service cloud provider
  * RHEL 8 on Google Cloud Provider
  * Ubuntu 18.04 and 20.04 on Google Cloud Provider
  * etc.

* EL7 and Amazon Linux 2: `clamonacc` executable fails with:

    ```
    Version of curl is too low to use fdpassing. Please use tcp socket streaming instead
    ```

    On-demand scanning with `clamscan` works, however.

* CentOS 8: `clamonacc` does not prevent access of files although `clamscan` works fine

## Requirements
In order to use the playbooks:
* Ansible 2.8+
* Your target systems must be:
  * Accessible by `ssh` without a password, probably with an ssh key
  * The default user is an unpriviledged user (not root)
  * Your default user can use `sudo` without a password to escalate priviledges to root

## Installation
This Ansible playbook installs the ClamAV packages on one or more target Linux servers with on-access scanning for user directories.  It heavily relies on https://github.com/geerlingguy/ansible-role-clamav and customizes the target system a little further.

### Instructions
```
$ git clone https://github.com/pfuntner/clamav-onacc.git
$ cd clamav-onacc.git
$ ansible-galaxy install -r requirements.yml -p roles
$ ansible-playbook -e hosts=server1,server2,... clamav-onacc.yml
```

### Testing
Once the `clamav-on-acc.yml` playbook is run, there are two playbooks you can use to test ClamAV

#### On-Access Scanning
##### Instructions
```
$ ansible-playbook -e hosts=server1,server2,... test-clamav-onacc.yml
```

#### On-Demand Scanning
##### Instructions
```
$ ansible-playbook -e hosts=server1,server2,... test-clamav-on-demand.yml
```
