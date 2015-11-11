In normal netcat, we can't specify source port, destination port, source MAC, destination MAC, sequence number, ttl etc

> However in scapy netcat all those options can be specified and this makes it more dangerous

> The following is the help file:
```
Script options
Where [required] and [[optional]] options are:

python nc --help
Script options
Where [required] and [[optional]] options are:
[[-h | --help]] for help message
[ -s | --src-ip] source IP
[ -d | --dest-ip] proxy IP
[[-r | --sport]] source port
[ -p | --dport] destination port
[[-1 | --src-mac]] source MAC Address
[[-2 | --dest-mac]] destination MAC Address
[[-t | --timeout]] timeout in seconds
[[-l | --ttl]] IP time-to-live value for packets
[[-q | --seqnum]] set sequence number of initial TCP packet
[[-v | --verbose]] show verbose output
[[-m | --timestring]] timestrings in log
[[-i | --setipt]] set iptables to reject RST packets from src host
[[-f | --sniff]] number of packets to sniff for
[[-n | --norcv]] Do an send instead of sr1 (send and receive)

```
> The following is a regular output:

```
echo -n -e "GET http://google.co.in HTTP/1.1\r\n\r\n" | python nc  -s 10.112.72.73 -d 10.112.251.130 -p 3128 -i --sniff 1 --norcv

HTTP/1.0 200 OK
Date: Tue, 21 Jun 2011 06:31:25 GMT
Server: Apache/2.2.9 (Debian)
X-UD-Host: webspace.udag.de
X-UD-Method: frame
X-UD-Target: http://www.cocostefan.de
Vary: Accept-Encoding
Content-Length: 431
Content-Type: text/html
X-Cache: MISS from <NOT DISPLAYED>
X-Cache-Lookup: MISS from <NOT DISPLAYED>:3128
Via: 1.1 <NOT DISPLAYED>:3128 (squid/2.7.STABLE6)
Connection: close

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
<html>
<head>
<title>Privat</title>
<META NAME="keywords" CONTENT="Stefan Beifuss; Corinna Gittner">
<META NAME="description" CONTENT="">
</head>

<frameset framespacing=0 frameborder=0 rows="100%,*" scrolling=NO noresize>
  <frame src="http://www.cocostefan.de">

<noframes>
Privat -  - coco.in</noframes>

</frameset>
</html>

```