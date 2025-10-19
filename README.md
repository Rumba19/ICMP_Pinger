# ICMP Pinger Lab

## Overview
A Python implementation of a ping application using ICMP (Internet Control Message Protocol) to test network connectivity and measure round-trip time (RTT) to remote hosts.

## Features
- Sends ICMP echo request packets to specified hosts
- Measures round-trip time for each packet
- Sends ping requests every second
- Handles packet loss with timeout detection (1 second)

## Requirements
- Python 3.x
- Administrator/root privileges (required for raw sockets)

## Usage

### Run the program:
```bash
sudo python3 icmp_pinger.py
```

### Test different hosts:
Edit the last line in the code to change the target:
```python
ping("google.com")      # Change to any host
ping("127.0.0.1")       # Localhost
ping("8.8.8.8")         # Google DNS
```

### Stop the program:
Press `Ctrl+C`

## Output
The program displays:
- Target IP address
- Round-trip time in seconds for each ping
- "Request timed out." if no response within 1 second

Example output:
```
Pinging 142.250.80.238 using Python:

0.025373935
0.020802021
0.013922214
```

## Implementation Details
- **ICMP Echo Request**: Type 8 packet sent to target
- **ICMP Echo Reply**: Type 0 packet received from target
- **Packet Structure**: Contains timestamp for RTT calculation
- **Timeout**: 1 second wait period for replies
- **Socket Type**: Raw socket (SOCK_RAW) for ICMP protocol

## Testing
Tested on hosts across different continents:
- North America: amazon.com
- Europe: bbc.co.uk
- Asia: baidu.com
- Australia: anu.edu.au


## Notes
- Raw sockets require elevated privileges
- Some networks/firewalls may block ICMP packets
- RTT values are displayed in seconds (multiply by 1000 for milliseconds)