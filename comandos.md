# Manual de Comandos  
## Topología 1
### Router  
____
Configuracione de las interfaces  
FastEthernet 0/0  
```
#conf t
#int f0/1
#ip address 192.168.1.250 255.255.255.0
#speed 100
#full-duplex
#no shutdown
```

FastEthernet 0/1.20  
```
#conf t
#int f0/1.20
#encapsulation dot1Q 20
#ip address 192.168.0.126 255.255.255.128

```

FastEthernet 0/1.50 
```
#conf t
#int f0/1.20
# encapsulation dot1Q 50
#ip address 192.168.0.190 255.255.255.192

```
Enrutamiento Dinamico:
```
#configure terminal
#router rip
#version 2
#network 10.0.0.0
#network 20.0.0.0
#network 192.168.0.0
#network 192.168.1.0
#network 192.168.2.0
#network 192.168.15.0
```
### ESW1
____
VLAN 20
```
#conf t
#vlan 20
#name Profesores
#end
```
VLAN 50
```
#conf t
#vlan 50
#name Estudiantes
#end
```
Puertos modo trunk
```
#Conf t
#interface range f1/0 / 15
#switchport mode trunk
#switcport trunk allowed vlan 1,20,50,1002-1005
#end
```

## Topología 2 
### Router 2  
____
Enrutamiento Dinamico: 
```
#configure terminal
#router rip
#version 2
#network 192.168.1.0
#network 10.10.0.0
#network 20.10.0.0

```
EIGRP 
```
#conf t
#router eigrp 10
#network 10.10.0.0 0.0.0.255
#network 20.10.0.0 0.0.0.255
#network 192.168.15.0 0.0.0.255
#end
```
Configuracione de las interfaces  
FastEthernet 0/1  
```
#conf t
#int f0/1
#ip address 10.10.0.1 255.255.255.0
#no shutdown
```
FastEthernet 1/0  
```
#conf t
#int f0/1
#ip address 20.10.0.5 255.255.255.0
#no shutdown
```
### Router 3
____
EIGRP 
```
#conf t
#router eigrp 10
#network 10.10.0.0 0.0.0.255
#network 20.10.0.0 0.0.0.255
#network 192.168.15.0 0.0.0.255
#end
```
VRRP 
```
#conf t
#vrrp 10
#vrrp 10 ip 192.168.15.3
#vrrp 10 priority 120
#vrrp 10 preempt
#end
```
Configuracione de las interfaces  
FastEthernet 0/0  
```
#conf t
#int f0/1
#ip address 10.10.0.10 255.255.255.0
#no shutdown
```
FastEthernet 0/1  
```
#conf t
#int f0/1
#ip address 192.168.15.1 255.255.255.0
#no shutdown
```
### Router 4
______
EIGRP 
```
#conf t
#router eigrp 10
#network 10.10.0.0 0.0.0.255
#network 20.10.0.0 0.0.0.255
#network 192.168.15.0 0.0.0.255
#end
```
VRRP 
```
#conf t
#vrrp 10
#vrrp 10 ip 192.168.15.3
#vrrp 10 priority 100
#vrrp 10 preempt
#end
```
Configuracione de las interfaces  
FastEthernet 0/0  
```
#conf t
#int f0/1
#ip address 20.10.0.1 255.255.255.0
#no shutdown
```
FastEthernet 0/1  
```
#conf t
#int f0/1
#ip address 192.168.15.2 255.255.255.0
#no shutdown
```
### ESW2 
_____
Interfaces
```
#conf t
#int range f1/0 - 3
#no shut
#end
```

Puertos en modo troncal
```
#conf t
#int range f1/2 - 3
#switchport mode trunk
#switchport trunk allowed vlan 1,70,1002-1005
#end
```