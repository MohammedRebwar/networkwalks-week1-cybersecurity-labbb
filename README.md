# Networkwalks Cybersecurity Internship

## Week 1 — Cybersecurity Lab Environment Setup

> **Intern:** Mohammed Rebwar
> **Program:** Networkwalks Cybersecurity Internship
> **Week:** 01
> **Lab Focus:** Virtualized Cybersecurity Environment

---

## 1. Overview

This project documents the setup of a dedicated cybersecurity laboratory environment using Oracle VirtualBox and Kali Linux.

The objective was to establish an isolated and reproducible virtual environment that can be used for cybersecurity learning, practical exercises, and future lab activities during the internship.

The environment was configured with a dedicated VirtualBox NAT Network and a static network configuration for the Kali Linux virtual machine.

## 2. Lab Objectives

* Install and prepare the required virtualization software.
* Deploy Kali Linux as a VirtualBox virtual machine.
* Create and configure a dedicated NAT Network.
* Configure static network connectivity inside Kali Linux.
* Verify the assigned IP address, gateway, and DNS configuration.
* Create a clean VirtualBox snapshot for the completed lab environment.

## 3. Lab Environment

| Component      | Configuration          |
| -------------- | ---------------------- |
| Host OS        | Windows 10/11          |
| Hypervisor     | Oracle VirtualBox      |
| Security OS    | Kali Linux 2026.2      |
| Network Type   | VirtualBox NAT Network |
| Network        | `10.0.0.0/24`          |
| Kali Interface | `eth0`                 |
| Kali IP        | `10.0.0.2/24`          |
| Gateway        | `10.0.0.1`             |
| DNS            | `8.8.8.8`              |

## 4. Network Architecture

```text
┌──────────────────────────────┐
│        Windows Host          │
│                              │
│       Oracle VirtualBox      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│       NatNetwork             │
│       10.0.0.0/24            │
│       Gateway: 10.0.0.1      │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        Kali Linux VM         │
│                              │
│  eth0: 10.0.0.2/24           │
│  DNS:  8.8.8.8               │
└──────────────────────────────┘
```

---
## 5. Implementation

### 5.1 7-Zip Installation

7-Zip was installed to provide archive extraction support for the Kali Linux VirtualBox package.

![7-Zip Installation](screenshots/01-7zip.png)

---

### 5.2 Oracle VirtualBox Installation

Oracle VirtualBox was installed as the virtualization platform used to deploy the cybersecurity laboratory environment.

![Oracle VirtualBox](screenshots/02-virtualbox.png)

---

### 5.3 NAT Network Configuration

A dedicated VirtualBox NAT Network named `NatNetwork` was created using the `10.0.0.0/24` network.

The network provides the virtual environment with connectivity through the configured gateway.

![NAT Network Configuration](screenshots/03-nat-network.png)

---

### 5.4 Kali Linux Virtual Machine

The Kali Linux 2026.2 VirtualBox image was extracted and imported into Oracle VirtualBox.

The VM's network adapter was connected to the previously created `NatNetwork`.

![Kali Network Adapter](screenshots/04-kali-network-adapter.png)

---

### 5.5 Kali Linux Network Configuration

The Kali Linux interface `eth0` was configured with a static IPv4 address.

| Parameter    | Value         |
| ------------ | ------------- |
| Interface    | `eth0`        |
| IPv4 Address | `10.0.0.2/24` |
| Network      | `10.0.0.0/24` |
| Gateway      | `10.0.0.1`    |
| DNS Server   | `8.8.8.8`     |

The configuration was verified from the Kali Linux terminal.

![Kali Network Configuration](screenshots/05-kali-network-configuration.png)

---

### 5.6 VirtualBox Snapshot

After completing the laboratory configuration, a VirtualBox snapshot named `Week1` was created.

The snapshot provides a clean recovery point for the completed Week 1 environment.

![Week 1 Snapshot](screenshots/06-kali-snapshot.png)

---
## 6. Verification

The completed laboratory environment was verified using Kali Linux networking commands.

### IP Address Verification

```bash
ip addr
```

The `eth0` interface was verified with the configured address:

```text
10.0.0.2/24
```

### Routing Verification

```bash
ip route
```

The default gateway was verified as:

```text
10.0.0.1
```

### DNS Verification

The DNS configuration was verified with:

```bash
cat /etc/resolv.conf
```

The configured DNS server was:

```text
8.8.8.8
```

These checks confirmed that the Kali Linux virtual machine was correctly configured within the `10.0.0.0/24` laboratory network.

---

## 7. Evidence

The repository contains screenshots documenting the major stages of the laboratory setup:

| Evidence                            | Description                            |
| ----------------------------------- | -------------------------------------- |
| `01-7zip.png`                       | 7-Zip installation                     |
| `02-virtualbox.png`                 | VirtualBox installation                |
| `03-nat-network.png`                | NAT Network configuration              |
| `04-kali-network-adapter.png`       | Kali VM network adapter                |
| `05-kali-network-configuration.png` | Kali IP, gateway and DNS configuration |
| `06-kali-snapshot.png`              | Completed Week 1 snapshot              |

---

## 8. Lessons Learned

During this lab, I gained practical experience with:

* Setting up a virtualized cybersecurity laboratory.
* Deploying Kali Linux in Oracle VirtualBox.
* Configuring a dedicated virtual network.
* Understanding IPv4 addressing and subnet configuration.
* Configuring a default gateway and DNS server.
* Using Linux networking commands to verify connectivity.
* Creating VM snapshots for environment recovery.

## 9. Final Status

**Week 1 Cybersecurity Lab Setup — Completed**

The laboratory environment is configured and preserved as a VirtualBox snapshot, providing a clean foundation for future cybersecurity exercises.

---

## Disclaimer

This laboratory environment is intended for authorized cybersecurity learning and internship activities. Testing should only be performed against systems and networks for which appropriate authorization has been provided.
