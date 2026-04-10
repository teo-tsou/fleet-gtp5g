# fleet-gtp5g

Fleet bundle to install the `gtp5g` kernel module on every K3s node.
Required by free5GC UPF for GTP-U tunnel support.

## What it does
- Runs as a DaemonSet on every node (including new nodes that join later)
- Installs kernel headers, build tools, and DKMS on the host
- Builds and installs gtp5g v0.9.5 via DKMS (persists across kernel upgrades)
- Loads the module immediately via `modprobe` (no reboot needed)
- Enables `net.ipv4.ip_forward` persistently

## Requirements
- Ubuntu 22.04 nodes
- Kernel 5.15.x
- Internet access from nodes (to apt-get and git clone)

## Add to Fleet
Rancher → Fleet → Git Repos → Add Repository:

| Field          | Value                                      |
|----------------|--------------------------------------------|
| Name           | `fleet-gtp5g`                              |
| Repository URL | `https://github.com/teo-tsou/fleet-gtp5g` |
| Branch         | `main`                                     |
| Paths          | `/`                                        |
