# transientBug Ansible

# Setup
```
$ brew install ansible
$ pip2 install requests --user
```

You'll need to have your DigitalOcean API Token in `$DO_TOKEN`
and you need the rails master key in `$RAILS_MASTER_KEY`.

# Usage
```
$ ansible-playbook staging.yml
```

## DO Groups
```
$ bin/digital_ocean.py --list | jq 'keys'
```
