Controller Configuration
=========


Playbooks
--------------
| Name | Description |
| :--- | :--- |
| `controller_config.yml` | After populating vars in contorller_vars directory, run this playbook to add the defined object definitions to your Automation Platform. |
| `hub_config.yml` | After populating vars in hub_vars directory, run this playbook to add the defined object definitions to your Automation Hub. |


Requirements
------------

This content utilizes the ansible.controller, infra.controller_configuration, and infra.ah_configuration collections.  You will need connectivity to a Private Automation Hub server which has synchronized these collections or to the internet so that the collections can be installed.

You will also need Automation Platform and / or Automation Hub credentials with sufficient permissions to create the objects you define as code.  For Automation Platform specificall, unless an Automation Platform system admin has enabled the setting `Allow External Users to Create OAuth2 Tokens` you will need to use a local account in the cluster and not an externally (such as ldap) authenticated account.

Input Variables
--------------

`controller_config.yml` variables:
----------
|Variable Name|Default Value|Required|Type|Description|
|:---:|:---:|:---:|:---:|:---:|
| `state` | 'present' | no | str | Create all objects or delete them.  Valid values are `absent` or `present` |
| `org_name` | '' | yes | str | Which organization in Automation Platform the objects defined should be assigned to. |


`hub_config.yml` variables:
----------
|Variable Name|Default Value|Required|Type|Description|
|:---:|:---:|:---:|:---:|:---:|
| `state` | 'present' | no | str | Create all objects or delete them.  Valid values are `absent` or `present` |


Dependencies
------------

A combination of `ansible.controller` and `controller_configuration` collections.

Playbook Execution
----------------

You can run this playbook from ansible cli or as a Job Template in Controller.

From the command line:

    `ansible-playbook controller_config.yml -e 'org_name=Default'`
    `ansible-playbook hub_config.yml`

License
-------

MIT

Author Information
------------------

Tony Reveal
