# tcpdump

## tcpdump info

#### version

```bash
tcpdump -h |& head  -n 3
```

#### available interfaces

```bash
tcpdump -D
```

## tcpdump capture

#### on a specific interface

```bash
tcpdump -i eth0
```

> -n  : don't convert addresses to names

```bash
sudo tcpdump -i eth0 -n
```

> -c <count> : Exit after capturing count packets

```bash
sudo tcpdump -i eth0 -n -c 5
```


#### packet capture size

> -s <len> : Capture up to len bytes per packet

```bash
sudo tcpdump -i eth0 -n -s96
```

*if using `-s 0` : use default capture size equals to 65535*


#### tcpdump output

> -t : Don't print timestamps

```bash
sudo tcpdump -i eth0 -n -s96 -t
```

> -e : Print link-level headers

```bash
sudo tcpdump -i eth0 -n -e ether host 70:71:bc:68:c0:fc
```

> -A : Print frame payload in ASCII
> -x : Print frame payload in hex
> -q : Quick output

## file capture

#### saving capture to a file

> -w <file> : Write captured packets to file

```bash
sudo tcpdump -i any -w capture.pcap -c20 -v
```

#### reading from capture file

> -r <file> : Read packets from file

```bash
sudo tcpdump -r capture.pcap -n
```

## tcpdump filters


Keyword | Description
-------|-------------
`[src|dst] host <host>` | Matches a host as the IP source, destination, or either
`[tcp|udp] [src|dst] port <port>` | Matches TCP or UDP packets sent to/from port
`[src|dst] net <network>/<len>` | Matches packets to or from an endpoint residing in network
`(ether|ip|ip6) proto <protocol>` | Matches an Ethernet, IPv4, or IPv6 protocol
`ether [src|dst] host <ehost> ` | Matches a host as the Ethernet source, destination,
 or either
`(ether|ip|ip6) proto <protocol>` | Matches an Ethernet, IPv4, or IPv6 protocol