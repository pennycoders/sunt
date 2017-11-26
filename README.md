# Sunt

SNMP Agent for Linux written in Rust.

# Intro

SNMP is still the common ground for getting data into various kinds of monitoring
systems. Sunt aims to be a modern SNMP agent that is aware of how things are run
nowadays, stripped to the essentials but adding features where they make sense.

# Supported tables:

* hrStorageTable
* dskTable
* diskIOTable
* ifTable

# Notable differences to net-snmpd

* Considerably faster response

* hrStorageTable:

    * Only actual mountpoints are included (no RAM etc).
    * Duplicate mountpoints (bind mounts) are filtered out (useful for Docker/LXC hosts).

* diskIOTable:

    * `dm-*` devices are reported as the actual device, e.g. `vghive/data` or `crypted_home`. 

* ifTable

    * Only Physical interfaces, Bridges and VLAN interfaces are exported (VM interfaces and VPN tunnels are filtered).