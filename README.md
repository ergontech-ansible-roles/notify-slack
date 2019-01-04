Notify Slack Role
=========

Sends a message via a web request to a configured slack channel.


Role Variables
--------------

```
# Required Vars
# @docs - https://api.slack.com/incoming-webhooks#advanced_message_formatting
notify_slack_token:

# Vars
notify_enabled -> default(true)
notify_user
notify_env
notify_color
notify_fields

# Example (notify_fields)
notify_fields:
  - title: Environment
    value: "{{ notify_env }}"
    short: True
  - title: Branch
    value: "{{ deploy_hash }}"
    short: True
```


Use Role
----------------

```
#Playbook
- hosts: all
  gather_facts: no
  pre_tasks:
    - block:
      - include_role:
          name: slack-notify
          tasks_from: notify-begin-deployment.yml
        ...
      rescue:
        - include_role:
            name: slack-notify
            tasks_from: notify-deploy-failure.yml
```

```
# requirments.yml

- src: https://github.com/ergontech-ansible-roles/notify-slack
  version: master
  name: notify-slack
```

License
-------

MIT
