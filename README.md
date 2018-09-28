# mage-grav
Ansible role to setup Grav (CMS). To configure this role, change the defaults, for example as follows:

```
grav_version: 1.5.1
grav_uri: https://github.com/getgrav/grav/releases/download/{{ grav_version }}/grav-admin-v{{ grav_version }}.zip
grav_owner: www-data
grav_group: www-data
grav_webserver: apache
grav_installs:
  - /var/www/vhosts/example.com
  - /var/www/vhosts/grav.site
```

This is mostly self-explanatory, apart from

- `grav_webserver`: if set to 'apache', it will install the distributed .htaccess file
- `grav_installs`: this is a list of target directories where you want to have grav deployed. 

## BEWARE

- This role will install Grav only into an EMPTY directory (`grav_installs` item)
- This role will try to update Grav in each non-empty `grav_installs` item by running `bin/gmp self-upgrade` and `bin/gmp update`