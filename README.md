# snmp

## Basic

| name | description | ubuntu install |
----|----|----
| snmpd | An extensible agent for responding to SNMP queries for management information | snmpd |
| snmptrapd | A daemon application for receiving SNMP notifications | snmptrapd |
| snmptrap | Sending and receiving traps, and acting upon them | snmp |
| snmpwalk | retrieving lots of data at once! | snmp |

## Setup at ubuntu16.04

### Install & configure snmptrapd

```
# install (If you want to recieve snmp trap, you only need to install snmptrapd and snmp)
sudo apt-get install -y snmp snmptrapd

# configure
sudo sed -i -e 's/#authCommunity log,execute,net public/authCommunity log,execute,net public/g' /etc/snmp/snmptrapd.conf
```

## How to use snmptrapd
```
sudo snmptrapd -f -Ls 1   ## When you want to output to syslog as a facility=1
sudo snmptrapd -f -Lo     ## When you want to get logs into standard output of this command

# Options (for detail please see man snmptrapd)
# -----------------------------------------
# -f: Do not fork() from the calling shell.
# -Ls 1: output to syslog facility 1
# -Ls 2: output to syslog facility 2
# -Ls 3: output to syslog facility 3
...
# -Lo: Log messages to the standard output stream.
# -Le: Log messages to the standard error stream.
```

## Reference
http://www.net-snmp.org/
