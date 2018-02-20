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


# Super Manual Prod Migration
##Old Host:

```
docker exec transientbugrails_postgres_1 pg_dump -U transientbug --create transientbug_production > postgres_backup_staging-<date>.sql
tar -zcvf dropzone_backup_staging-<date>.tar.gz storage
```

`scp` data over from old host to the new host

## New Host:

```
cd /opt/transientbug/
tar -zxvf dropzone_backup_staging-<date>.tar.gz
mv storage/* /mnt/production-storage/
docker-compose down
docker volume prune
docker-compose up -d
cat postgres_backup_staging-<date>.sql | docker exec -i transientbug_postgres_1 psql -U transientbug
```
