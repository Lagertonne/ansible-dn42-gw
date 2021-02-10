dn42-gw
=========
Configures a dn42-gateway on debian, with ifupdown, wireguard and frr


Requirements
------------

You need wireguard and frr installed. You also need to generate the wireguard keys by yourself.

Role Variables
--------------
```
dn42:
  as: 4242423767 # your own AS number
  subnet: 172.21.74.128/26 # The subnet you want to route. Only one is currently supported
  local_ip: 172.21.74.129 # The IP of your host
  peers:
    - peername: xyz # freely adjustable name
      as: 4242423914 # remote as
      source_ip: 172.21.74.129 # source ip to set in frr and the SNAT. Dunno if this is necessary
      wg_port: 51832 # Local Wireguard Port to listen on if necessary. Not Necessary if we don't want to accept incoming connections
      local:
        ip_v4: 192.168.218.26 # IP Address of local wireguard client
        privkey: "" # Wireguard Private Key
        pubkey: "" # Wireguard Public IP
      peer:
        endpoint: "de2.g-load.eu:23767"
        ip_v4: 172.20.53.97
        pubkey: "B1xSG/XTJRLd+GrWDsB06BqnIq8Xud93YVh/LYYYtUY="    
```

Dependencies
------------
Nope.

Example Playbook
----------------

License
-------

BSD

Author Information
------------------
lagertonne
