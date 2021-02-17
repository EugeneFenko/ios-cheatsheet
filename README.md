# Cisco IOS Cheatsheets

## Enable (priv mode)

``` sw> enable ```

## Global configure

``` sw# configure terminal ```

## Set hostname

``` sw(config)# hostname sw-lan-1fl ```

## Enable interface

```code
sw(config)#interface fastEthernet 0/0
sw(config-if)#no shutdown
```

## Set IP address

```code
rt(config-if)#ip address 192.168.0.1 255.255.255.0
```

## Create subinterface

```code
rt(config)#interface fa0/0.2
rt(config-if)#description Management
rt(config-if)#encapsulation dot1Q 2
```

## Add vlan

```code
sw(config)# vlan NUMBER
sw(config-vlan)# name NAME
```

## Vlan to interface (Access)

```code
sw#interface fa0/1
sw(config)#description “I am using simple frames”
sw(config-if)#switchport mode access
sw(config-if)#switchport access vlan 2
```

## Vlan to interface (Trunk)

Enable trunk mode:

```code
Switch(config)#interface fa0/2
Switch(config-if)#description “I am using tagged frames”
Switch(config-if)#switchport mode trunk
```

Allow vlan to trunk:

```code
sw(config)#interface FastEthernet0/24
sw(config-if)# description sw
sw(config-if)# switchport trunk allowed vlan 2-3,101-104
sw(config-if)# switchport mode trunk
```

## Etherchannel

Config:

```code
sw(config-if)# channel-group <channel-group-number> mode <<auto [non-silent] | 
desirable [non-silent] | on> | <active | passive>>

```

Show:

```code
sw# show etherchannel summary
sw# show etherchannel port-channel
sw# show etherchannel detail
```

# Security

## Port security

```code
sw(config)# switchport port-security
sw(config)# switchport port-security maximum 1
sw(config)# switchport port-security mac-address MAC
sw(config)# switchport port-security mac-address sticky
sw(config)# switchport port-security violation {shutdown | restrict | protect}
```

## DHCP Snooping

```code
sw(config)# ip dhcp snooping
sw(config)# ip dhcp snooping vlan NUMBER
sw(config)# ip dhcp snooping trust
```

## IP Source Guard

```code
sw(config)# ip verify source
sw(config)# ip verify source port-security
```

## Dynamic ARP Inspection

```code
sw(config)# ip arp inspection vlan NUMBER
sw(config)# ip arp inspection trust
```
