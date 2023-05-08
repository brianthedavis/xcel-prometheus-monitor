# Testing Connectivity to the Meter

Prior to Launchpad Enrollment, the meter WILL show up as connected to your wifi, however the necessary ports won't be open yet.

## Find the Address

The first step to test connectivity is to obtain the IP address of the meter.  This will vary greatly depending on your network setup -- the easiest way is probably to poke around your router's web page to look for newly connected devices or however DHCP addresses are handed out on your network.  You can use a tool such as [maclookup.app](https://maclookup.app/search) to lookup any MAC addresses that are on your network.  The Vendor Name will show up as `Itron Inc` if you locate the correct device.

## Checking for connectivity

You can test connectivity with the following command (assuming the IP address is `10.0.20.208`)

```
sudo nmap -sT -p8081 -Pn 10.0.20.208
```

If you are not yet enrolled, you'll see a response like:

```
Starting Nmap 7.93 ( https://nmap.org ) at 2023-04-22 15:12 MDT
Nmap scan report for 10.0.20.208
Host is up.

PORT     STATE    SERVICE
8081/tcp filtered blackice-icecap
```

The key is the `STATE` of `filtered`, meaning port 8081 is not yet open.  Once you receieve your enrollment email, the response should appear as

```
Starting Nmap 7.80 ( https://nmap.org ) at 2023-05-02 18:59 MDT
Nmap scan report for10.0.20.208
Host is up (0.22s latency).

PORT     STATE SERVICE
8081/tcp open  blackice-icecap
```
