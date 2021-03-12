# clamav-onacc

## Supported Linux distros
* CentOS 8
* Debian 9
* Debian 10
* Ubuntu 16.04
* Ubuntu 18.04
* Ubuntu 20.04

### Qualified support
There is qualified support for other distros:
* `clamonacc` executable fails on EL7 and Amazon Linux 2:

    ```
    Version of curl is too low to use fdpassing. Please use tcp socket streaming instead
    ```

    On-demand scanning with `clamscan` works, however.

* RHEL 8 packages are not available on the Amazon Web Service could provider

* `clamonacc` does not prevent access of files on CentOS 8 although `clamscan` works fine

## Installation
This Ansible playbook installs the ClamAV packages on one or more target Linux servers with on-access scanning for user directories.  It heavily relies on https://github.com/geerlingguy/ansible-role-clamav and customizes the target system a little further.

### Instructions
```
$ git clone https://github.com/pfuntner/clamav-onacc.git
$ cd clamav-onacc.git
$ ansible-galaxy install -r requirements.yml -p roles
$ ansible-playbook -e hosts=server1,server2,... clamav-onacc.yml
```

## Testing
Once the `clamav-on-acc.yml` playbook is run, there are two playbooks you can use to test ClamAV

### On-Access Scanning
#### Instructions
```
$ ansible-playbook -e hosts=server1,server2,... test-clamav-onacc.yml
```

### On-Demand Scanning
#### Instructions
```
$ ansible-playbook -e hosts=server1,server2,... test-clamav-on-demand.yml
```
