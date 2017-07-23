# salt-vagrant

## Overview

Create simple lab for develope Saltstack's states

## IPs
```
master - 192.168.33.5
minion - 192.168.33.6
```

## Commands

### Run salt from master

```
salt minion1 state.highstate --state_output=mixed
salt minion state.sls 
```

### Run salt from minion - testing (no changes on machine)

```
salt-call state.highstate test=TRUE
salt-call state.highstate test
```

### Show pillar on master

```
salt-run pillar.show_top
salt-run pillar.show_top
```

### Show pillar on minion

```
salt-call pillar.items
salt-call pillar.get dns_servers
```

### Run salt highstate from master

```
salt '*' state.apply
salt '*' state.highstate
```

### Run exact state 

```
salt '*' state.apply mysql.server
salt-call state.apply mysql.server
```

### Run command via salt-ssh

```
salt-ssh client2 cmd.run 'ping -c 3 wp.pl'
```

### Debug apache formula (Jinja, Yaml, salt state):

```
salt '*' state.show_sls apache
```

### Debug master:

```
salt master1 state.highstate -l debug
```

### Template:
  https://github.com/saltstack-formulas/template-formula


