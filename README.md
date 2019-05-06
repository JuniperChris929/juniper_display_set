# Juniper display set

This script converts standard Juniper config into a list of 'set' commands which you can use 
to configure a Juniper device


Changelog 06.05.2019
-----
Migrated Script to python3



Usage
-----
The input is a standard Juniper configuration file like:

```
/* my configuration */
version 19.1R1;
system {
    host-name vSRX3.0;
    root-authentication {
        encrypted-password "$1$YJ7i1337Vpo8$myuAjTW/tkWlm6EudqcP4/"; ## SECRET-DATA
    }
    login {
        user dev {
            uid 1337;
            class super-user;
            authentication {
                encrypted-password "$1$YJ7i1337Vpo8$myuAjTW/tkWlm6EudqcP4/"; ## SECRET-DATA
            }
        }
    }
}
interfaces {
    ge-0/0/1 {
        vlan-tagging;
    }
    ge-0/0/2 {
        vlan-tagging;
    }
}
```


Run the Script with the example-non-set command as input file: junos-converter30.py example-in.conf
The output will be set-commands that you can use for your JunOS Device



Notes
-----
- Annotations will be lost (like /* my configuration */)
- Inactive blocks are supported (like "system syslog" in the example)
- Protect blocks are supported as well (like "system services" in the example)
- only non-set to set. The other way is currently a WIP
