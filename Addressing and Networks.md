## Names and Addresses
### Intro
DNS - Domain Name System

`host` is a utility for DNS lookups to convert names to IP addresses and vice versa
  - ``dig`` is more technical
- ``man host`` - for info

# Addressing and Networks
## Netblocks and Subnets
larger the network - shorter the prefix of the IP address

## IPv4 32bit
How many adresses are avalible for hosts on a network
- /(prefix) network = (32-prefix) bits of host part
  -  2^(32-prefix)-3 reserved = number of addresses avalible for hosts
### bibuup
`ip addr show` to find out what interfaces your machine has

`ip route show default` or `netstat -nr` to find your default gateway

## IPv4 private & public
RFC 1918 addresses - to look up private IP address information

my ip address - to look up your public IP address

### Windows Command Prompt - to look up private IP address
1. Click the Start button and type "CMD" into the search box/windows

2. CMD or Command Prompt will be shown in the menu. Right Click, and select Run as Administrator
 
3. Select "Yes" on the security confirmation message to continue.

4. In the command prompt, you will need to type this command: "ipconfig" then press Enter

## IPv6 128bit
http://test-ipv6.com/ to check whether your divice has IPv6 access
- while building an application you must account for the usage of IPv6 in the future
