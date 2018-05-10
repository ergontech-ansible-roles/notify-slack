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
# requirments.yml

- src: https://github.com/ergontech-ansible-roles/notify-slack-role
  version: master
  name: notify-slack
```

License
-------

MIT
