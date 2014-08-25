Ansible Fail2Ban Role
=====================

An ansible role for installing and configuring fail2ban. This role enables you to customize your local jail as well
as configuring custom filters and actions.

For more information on Fail2Ban, [visit the Fail2Ban website](http://www.fail2ban.org/wiki/index.php/Main_Page)

Role Variables
--------------

- fail2ban_path: path where Fail2Ban is installed on the remote host(s)
- fail2ban_filter_path: path where Fail2Ban stores all filters on the remote host(s)
- fail2ban_action_path: path where Fail2Ban stores all actions on the remote host(s)
- fail2ban_pkg_state: indicates the package state; Allowed setting: installed, latest
- fail2ban_pkg_version: specify the specific package version you wish to install
When specifying a version, the state will be forced to installed. When omitting the variable or leaving it empty
it will install the package as specified by the state variable 
- fail2ban_service_state: indicates the service state; Allowed setting: started, stopped 
- fail2ban_service_enabled: indicates if service needs to be enabled on boot; Allowed settings: yes, no
- fail2ban_config: is a dict that can hold all settings for your jail.local file
- fail2ban_filters: is a dict that can hold all filters that need to be configured in your jail.local file.
The dict key will be used as section name and filter value. So make sure this matches. 
The filter key will also be used to check if there are any custom filters that need to be copied to the remote host(s)
Your custom filters should be stored under files/filters
- fail2ban_actions: holds a list with all custom actions that need to be copied to the remote host(s). 
Your custom actions should be stored under files/actions

View the default vars - defaults/main.yml - for a more detailed example.


Example Playbook
-------------------------

    - hosts: servers
      roles:
         - { role: michaelrigart.fail2ban }

License
-------

GPLv3

Author Information
------------------

Michaël Rigart <michael@netronix.be>