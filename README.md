# deploy-seed
A simple way to deploy to any remote server using Git and Ansible. Tested with servers running Ubuntu 14.04 LTS.

## Set up remote machine

1. Create a file `hosts` in the `ansible` directory to configure server(s). Example:

```
# ansible/hosts
host-01 ansible_host=00.00.000.000 ansible_user=ubuntu ansible_ssh_private_key_file=../private/key.pem
```

1. Optionally, create a directory named `ansible/private` (automatically git ignored) to store private keys and other data.

1. Configure `ansible/site.yml` with a `project_alias` (will be used to name folders on the remote machine).

1. To deploy, run the deploy script:

```
. deploy.sh
```

## Local machine

1. `cd` into the git repo that you want to push to your remote server and add a new `remote` called `live` (or similar):

```
git remote add live ssh://ubuntu@[IP_ADDRESS]/var/repo/[PROJECT_ALIAS].git
```

1. And that's it! You can deploy your code to your server:

```
git push live master
```
