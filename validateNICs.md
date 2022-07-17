# validateNICs

### Gateway

It seems gateway is running linux of some sort. For gateway this function checks if the specific interface (enp1s0f0) is up. Then, if it's ipv4 address is different than localhost, it sets proper options in system.json and continues.

### Server

First the function uses ipinfo.exe to get a list of interfaces, then filters out VirtualBox host-only ones. There's a lot of logic in selecting the proper interface then - best to look at the source.
