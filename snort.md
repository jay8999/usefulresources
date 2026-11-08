# Snort IDS Rule Cheat Sheet & Notes

Snort is an open-source Network Intrusion Detection and Prevention System (IDS/IPS) capable of performing real-time traffic analysis and packet logging on IP networks.

## 1. Anatomy of a Snort Rule

Every Snort rule consists of two main logical parts: the **Rule Header** and the **Rule Options**.

```text [action] [protocol] [source-ip] [source-port] [direction] [destination-ip] [destination-port] ([options])```
Example Rule:
Code snippet
alert tcp any any <> any any (msg:"Flag Push-Ack Test"; flags:P,A; sid:1000003; rev:1;)

## 2. Rule Header Breakdown
Component	Values / Examples	Description
Action	alert, log, pass, drop, reject	Tells Snort what to do when a packet matches the rule. (alert generates an alert and logs the packet).
Protocol	tcp, udp, icmp, ip	Specifies the network protocol to inspect.

Source IP	any, 192.168.1.0/24, [10.0.0.1,10.0.0.2]	The source IP address filter. any matches all IPs.
Source Port	any, 80, 1024:65535	The source port filter. Ranges can be specified using a colon (:).

Direction	->, <>	Traffic direction operator. -> means source to destination; <> means bidirectional (both directions).
Destination IP	any, 192.168.1.50	The target IP address filter.
Destination Port	any, 443, !22	The target port filter (exclamation mark ! means "not").

## 3. Common Rule Options
Rule options form the core matching logic and metadata for the rule, enclosed in parentheses (...) and separated by semicolons (;).

msg: Defines the descriptive message text that appears in logs or alerts when the rule triggers.

Example: msg:"Sus IP ID found";

flags: Inspects TCP header flags. Multiple flags can be comma-separated.

S = SYN (Synchronize)

A = ACK (Acknowledgment)

P = PSH (Push)

F = FIN (Finish)

R = RST (Reset)

U = URG (Urgent)

Example: flags:P,A; (Matches packets where both Push and ACK are set)

sid (Snort ID): A unique numerical identifier for the rule. Custom/local rules typically start at 1000001 to avoid conflicting with official Snort rules.

Example: sid:1000003;

rev (Revision): Tracks how many times the rule has been updated or modified.

Example: rev:1;

id: Matches a specific decimal value within the IP header Identification field.

Example: id:35369;

## 4. Practical Rule Examples

A. ICMP ID Rule (Anomalous IP ID Check)
Code snippet
alert icmp any any <> any any (msg:"Sus IP ID found"; id:35369; sid:1000001; rev:1;)
Purpose: Triggers on any ICMP traffic where the IP header ID field matches 35369, which can sometimes indicate custom scripts, covert data channels, or device fingerprinting.

B. TCP SYN Flag Rule (Handshake Monitoring)
Code snippet
alert tcp any any <> any any (msg:"Flag SYN Test"; flags:S; sid:1000002; rev:1;)
Purpose: Flags any TCP packet with the SYN flag turned on (the first step of establishing a standard TCP connection). Useful in lab environments or port scan tracking.

C. TCP Push-Ack Flag Rule (Active Stream Inspection)
Code snippet
alert tcp any any <> any any (msg:"Flag Push-Ack Test"; flags:P,A; sid:1000003; rev:1;)
Purpose: Triggers when both PSH and ACK flags are active simultaneously, helping analysts monitor non-standard traffic patterns or specific data streaming behaviors.
