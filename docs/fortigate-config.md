# CONFIGURATION FORTIGATE 

### Create Configuration Port1 (WAN)
- config system interface
- edit port1
- set mode dhcp
- set allowaccess ping https ssh
- next
- end

### Create Configuration Port2 (LAN)
- config system interface
- edit port2
- set ip 10.200.200.1 255.255.255.0
- set allowaccess ping https ssh
- next
- end

### Configuration DNS 
- config system dns
- set primary 8.8.8.8
- set secondary 1.1.1.1
- end

### Static Route
- config router static
- edit 1
- set dst 0.0.0.0 0.0.0.0
- set gateway 192.168.5.2
- set device port1
- next
- end

### Firewall Policy
### CREATE POLICY SERVER TO INTERNET
- config firewall policy
- edit 1
- set name SERVER-INTERNET
- set srcintf port2
- set dstintf port1
- set srcaddr all
- set dstaddr all
- set action accept
- set schedule always
- set service ALL
- set nat enable
- next
- end
