# VLAN Configuration Exporter

A Python tool that connects to **Cisco** and **Aruba AOS-CX** switches via SSH, extracts all VLAN SVI (Layer 3) interface data, displays it in a clean terminal table, and exports it to a timestamped Excel file.

---

## Supported Vendors

| Vendor | Option | Platform |
|---|---|---|
| Cisco IOS / IOS-XE | `cisco` | Any Cisco Layer 3 switch |
| Aruba AOS-CX | `aruba_cx` | 8xxx / 6xxx / 4xxx series |

---

## Features

- SSH connection using Netmiko
- Extracts VLAN, IP Address, Subnet Mask, Virtual IP, Priority, Preempt, Status
- Detects HSRP (Cisco) and Active-Gateway / VRRP (Aruba CX) virtual IPs
- Clean terminal table output with Active / Shutdown summary
- Auto-named Excel export: `vlan_export_<IP>_<timestamp>.xlsx`
- Graceful error handling for failed connections and empty results


---

## Requirements

```bash
pip install netmiko pandas openpyxl
```

---

## Usage

```bash
python vlan_exporter.py
```

```
╔══════════════════════════════════════════════╗
║        VLAN Configuration Exporter           ║
║           Cisco  |  Aruba AOS-CX             ║
╚══════════════════════════════════════════════╝

  Switch IP Address : 192.168.10.1
  Vendor options    : cisco | aruba_cx
  Vendor            : aruba_cx
  Username          : admin
  Password          :

  Connecting to 192.168.10.1 ...
  Connected successfully.
  Retrieving VLAN data ...

  Found 10 VLAN(s)  —  9 Active  /  1 Shutdown

+--------+---------------+---------------+----------------+----------+---------+----------+
| VLAN   | IP Address    | Subnet Mask   | Virtual IP     | Priority | Preempt | Status   |
+--------+---------------+---------------+----------------+----------+---------+----------+
| Vlan10 | 192.168.10.2  | 255.255.255.0 | 192.168.10.254 |          | No      | Active   |
| Vlan20 | 192.168.20.2  | 255.255.255.0 | 192.168.20.254 |          | No      | Active   |
| Vlan30 | 192.168.30.2  | 255.255.255.0 | 192.168.30.254 |          | No      | Active   |
| Vlan40 | 192.168.40.2  | 255.255.255.0 | 192.168.40.254 |          | No      | Active   |
| Vlan50 | 192.168.50.2  | 255.255.255.0 | 192.168.50.254 |          | No      | Active   |
| Vlan60 | 192.168.60.2  | 255.255.255.0 | 192.168.60.254 |          | No      | Active   |
| Vlan70 | 192.168.70.2  | 255.255.255.0 | 192.168.70.254 |          | No      | Active   |
| Vlan80 | 192.168.80.2  | 255.255.255.0 | 192.168.80.254 |          | No      | Active   |
| Vlan90 | 192.168.90.2  | 255.255.255.0 |                |          | No      | Active   |
| Vlan99 | 192.168.99.2  | 255.255.255.0 |                |          | No      | Shutdown |
+--------+---------------+---------------+----------------+----------+---------+----------+

  Export saved to: vlan_export_192.168.10.1_20260213_143022.xlsx
  Done.
```

---


