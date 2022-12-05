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
