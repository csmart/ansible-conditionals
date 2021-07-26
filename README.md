# Simple playbook to show conditionals

This is just to show how you can set a variable and perform tasks, import roles
and or other plays.

This just runs on localhost and prints out when it's going to "do a thing."

## Do not do a thing

This is the default, just run the ansible.


```bash
ansible-playbook -i localhost, -c local site.yml
```

This will result like so.

```

PLAY [all] ******************************************************************************************************```*

TASK [From task] *************************************************************************************************
skipping: [localhost]

TASK [From task] *************************************************************************************************
ok: [localhost] => {
    "msg": "We are NOT doing a thing in a task"
}

TASK [test : From role] ******************************************************************************************
skipping: [localhost]

PLAY [all] *******************************************************************************************************

TASK [From play] *************************************************************************************************
skipping: [localhost]

PLAY RECAP *******************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=3    rescued=0    ignored=0   

```

## Do a thing

Execute ansible with the argument.

```bash
ansible-playbook -i localhost, -c local site.yml -e do_thing=true
```

This should result in the following.

```
PLAY [all] *******************************************************************************************************

TASK [From task] *************************************************************************************************
ok: [localhost] => {
    "msg": "We are doing a thing in a task"
}

TASK [From task] *************************************************************************************************
skipping: [localhost]

TASK [test : From role] ******************************************************************************************
ok: [localhost] => {
    "msg": "We are doing a thing in a role"
}

PLAY [all] *******************************************************************************************************

TASK [From play] *************************************************************************************************
ok: [localhost] => {
    "msg": "We are doing a thing in a play"
}

PLAY RECAP *******************************************************************************************************
localhost                  : ok=3    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0   
```
