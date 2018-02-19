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

```
tar -zxvf dropzone_backup_staging-2018-02-19.tar.gz
mv storage/* /mnt/production-storage/
cat postgres_backup_staging-2018-02-19.sql | docker exec -i transientbug_postgres_1 psql -U transientbug -d transientbug_production
```
