# Blog Infrastructure
Some fancy scripts and yamls for my blog infrastructure... gosh just use docker already, Jesus.

## Requirements

* `ansible` v2.12+

## Keys

Key generation:

```sh
ssh-keygen -t ed25519 -C "user@example.com" -f ./keys/production_key
ssh-keygen -t ed25519 -C "user@example.com" -f ./keys/staging_key
```

Key naming:

* `production_key` — SSH key for production `deploy` user
* `staging_key` — SSH key for staging `deploy` user

**Note: `./keys/` folder should be added to `.gitignore`!**

## Provision

Some steps are still manual, host that needs to be provisioned have to have `deploy` user.

To provision staging environment:

```commandline
ansible-playbook staging-provision.yml 
```

Another manual step is to run `pm2 startup` command and follow its instruction.

The same goes for production environment, but `production-provision.yml` playbooks needs to be used.

### Environment variables

Sometimes PM2 doesn't start services with new environment variables,
to force variables update command below needs to be run:

```commandline
ansible staging -a "pm2 restart all -a"
```
