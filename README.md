# clamav-onacc

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
Once the `clamav-on-acc.yml` playbook is run, you can test that on-access scanning is working by running another playbook.

### Instructions
```
$ ansible-playbook -e hosts=server1,server2,... test-clamav-onacc.yml
```
