# Network PortScanning
# PortPhantom

**PortPhantom** is a powerful, multi-threaded port scanner written in Python. It supports TCP and UDP scanning with service detection via banner grabbing.

### Features
- TCP and UDP scanning
- Service version detection
- Port range customization
- Fast multi-threading
- Clean, readable output

### Usage

```bash
python3 portphantom.py <target> -p <port-range> [-u] [-t timeout]


python3 portphantom.py 192.168.1.1 -p 20-80
python3 portphantom.py example.com -p 53,67,161 -u


