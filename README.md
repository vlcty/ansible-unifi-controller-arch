# ansible-unifi-controller-arch

This playbook installs an UniFi Controller on Arch Linux. It's achieved by downloading the Debian package, extracting it and do a few Arch Linux specific changes. A systemd unit file (unifi.service) is also included.

As a litte bonus you are able to generate a key store out of an existing private/public key if you want to have proper HTTPS/TLS.

## Available variables

|  Variable | Explanation | Default value |
|-----------|-------------|---------------|
| unifi_version | Which version to install | 5.5.20
| unifi_temp_path | Where to unpack the debian package and so on | /usr/share/unifi-temp
| unifi_generate_keystore | Should a key store be generated | false |
| unifi_keystore_private_key | (Local) location of the private key for the keystore | private.pem |
| unifi_keystore_cert | (Local) location of the certificate for the key store | public.pem |
| unifi_keystore_ca | (Local) location of the CA Certificate(s) for the key store | ca.pem |

The ```unifi_keystore_*``` variables are only used when ```unifi_generate_keystore``` is set to ```true```

## Updating UniFi

Updating the WebGui with this role should be no problem. However, this is not fully tested. Sorry :-)

## Tests

Use Vagrant to spin up a local Arch Linux virtual machine. A Vagrantfile is provided.

Example:
```
:~$ vagrant up
<vagrant working. Wait until you get the bash prompt back>
:~$ ansible-playbook -i testinventory deploy-unifi.yml
```

After the playbook is finished you should be able to access the UniFi Web GUI unter ```https://127.0.0.1:8443```
