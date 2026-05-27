# Ansible for Junos OS Developer Guide Examples

A complete collection of Ansible playbooks sourced directly from the
**Juniper Networks Ansible for Junos OS Developer Guide**, covering all modules in the [`juniper.device`](https://galaxy.ansible.com/ui/repo/published/juniper/device/)
collection. Published on 2025-09-02.

Every playbook includes the source page name, page number, and URL in its header comments. The developer guide PDF is included in this folder for reference.

There are minor changes made to the playbooks which include:
- indentation adjustments
- addition of FQCNs that are documented in the 3 playbooks altered
 
---

## Source Documentation

[Ansible for Junos OS Developer Guide (PDF)](ansible.pdf)  
[Developer Guide (HTML)](https://www.juniper.net/documentation/us/en/software/junos-ansible/ansible/topics/concept/junos-ansible-overview.html)

---

## Prerequisites

| Requirement | Notes |
|---|---|
| Ansible | 2.17 or later |
| `juniper.device` collection | `ansible-galaxy collection install juniper.device` |
| `junos-eznc` >= 2.5.2 | `pip install junos-eznc` |
| Python 3 | Required on the Ansible control node |
| NETCONF enabled on Junos devices | `set system services netconf ssh` |
| SSH key pair (recommended) | Configure the public key on each Junos device |
| JSNAPy (jsnapy_* playbooks only) | `pip install jsnapy` |

---

## Module Coverage

| Module | Description | Playbooks |
|---|---|---|
| `command` | Execute CLI commands | `command_basic.yml`, `command_dest_dir.yml` |
| `config` | Manipulate device configuration | `config_*.yml`, `retrieve_*.yml`, `compare_to_rollback.yml` |
| `facts` | Retrieve device facts | `facts_basic.yml`, `facts_with_config.yml` |
| `file_copy` | Copy files to/from a device | `file_copy_get.yml`, `file_copy_put.yml` |
| `jsnapy` | Execute JSNAPy snapshot tests | `jsnapy_*.yml`, `jsnapy_bgp_example.yml` |
| `rpc` | Execute NETCONF RPCs | `rpc_*.yml` |
| `software` | Install Junos OS software | `software_*.yml` |
| `system` | Reboot / halt / shutdown / zeroize | `system_*.yml`, `system_*.yml` |
| `table` | Retrieve data via PyEZ tables | `table_*.yml` |

---

## Playbooks by Section

### Use Ansible to Connect to Junos Devices
*Chapter 4 — Pages 29–37*

| Playbook | Page | Description |
|---|---|---|
| `connect_persistent_pyez.yml` | 32 | Persistent juniper.device.pyez connection |
| `connect_ssh_default_keys.yml` | 33 | SSH with default keys |
| `connect_ssh_console_server.yml` | 33–34 | SSH through a console server |
| `connect_ssh_custom_config.yml` | 35 | SSH with a custom SSH config file |
| `connect_telnet.yml` | 35–36 | Telnet connection |
| `connect_serial_console.yml` | 36–37 | Serial console connection |

### Authenticate Users Executing Ansible Modules on Junos Devices
*Chapter 4 — Pages 37–51*

| Playbook | Page | Description |
|---|---|---|
| `auth_persistent_pyez_vars.yml` | 41–42 | pyez with vars section |
| `auth_password_prompt.yml` | 45–46 | Interactive username/password prompt |
| `auth_ask_pass.yml` | 46–47 | Run with --ask-pass CLI option |
| `auth_vault.yml` | 48 | Ansible vault-encrypted credentials |
| `auth_console_server_vault.yml` | 49–50 | Console server with vault credentials |

### Use Ansible to Retrieve Facts from Junos Devices
*Chapter 5 — Pages 52–55*

| Playbook | Page | Description |
|---|---|---|
| `get_device_facts.yml` | 11 | Foundational getting-started example |
| `facts_basic.yml` | 53 | Retrieve and save device facts |
| `facts_with_config.yml` | 53–54 | Retrieve facts and active configuration |

### Use Ansible to Execute Commands and RPCs on Junos Devices
*Chapter 5 — Pages 55–65*

| Playbook | Page | Description |
|---|---|---|
| `command_basic.yml` | 56 | Execute operational mode commands |
| `rpc_basic.yml` | 57 | Execute a single RPC |
| `rpc_kwargs.yml` | 58 | Multiple RPCs with per-RPC kwargs |
| `rpc_formats_same.yml` | 61 | RPCs with a single shared format |
| `rpc_formats_mixed.yml` | 61–62 | RPCs with per-RPC formats |
| `rpc_dest_dir.yml` | 63 | Save RPC output to dest_dir |
| `command_dest_dir.yml` | 63–64 | Save command output to dest_dir |
| `rpc_dest.yml` | 64 | Save all RPC output to a single dest file |

### Use Ansible to Transfer Files to or from Junos Devices
*Chapter 5 — Pages 65–69*

| Playbook | Page | Description |
|---|---|---|
| `file_copy_get.yml` | 66–67 | Download a file from the device |
| `file_copy_put.yml` | 68 | Upload a file to the device |

### Use Ansible with Junos PyEZ Tables to Retrieve Operational Information from Junos Devices
*Chapter 5 — Pages 69–75*

| Playbook | Page | Description |
|---|---|---|
| `table_arp.yml` | 72 | ARP table (ArpTable) |
| `table_ospf.yml` | 73 | OSPF interface table (OspfInterfaceTable) |
| `table_ethport.yml` | 74 | Ethernet port table with kwargs |

### Use Ansible to Halt, Reboot, or Shut Down Junos Devices
*Chapter 5 — Pages 75–88*

| Playbook | Page | Description |
|---|---|---|
| `system_reboot_immediate.yml` | 76 | Immediate reboot |
| `system_reboot_in_min.yml` | 77 | Reboot after delay (in_min) |
| `system_reboot_all_re.yml` | 78–79 | Reboot all Routing Engines |
| `system_reboot_vmhost.yml` | 79–80 | Reboot VM host |
| `system_reboot_example.yml` | 84–85 | Full reboot example with confirmation + handlers |

### Use Ansible to Install Software on Junos Devices
*Chapter 5 — Pages 88–107*

| Playbook | Page | Description |
|---|---|---|
| `software_basic.yml` | 91–92 | Basic Junos OS upgrade |
| `software_kwargs.yml` | 94–95 | Upgrade with kwargs (unlink: true) |
| `software_vmhost.yml` | 95 | VM host upgrade |
| `software_issu.yml` | 96 | Unified ISSU |
| `software_nssu.yml` | 96–97 | NSSU |
| `software_ex_vc_members.yml` | 97–98 | Upgrade specific EX VC members |
| `software_install_example.yml` | 101–102 | Full install example with handler |

### Use Ansible to Restore a Junos Device to the Factory-Default Configuration Settings
*Chapter 5 — Pages 107–115*

| Playbook | Page | Description |
|---|---|---|
| `system_zeroize.yml` | 108 | Zeroize all REs (factory reset) |
| `system_zeroize_connected_re.yml` | 108–109 | Zeroize connected RE only |
| `system_zeroize_media.yml` | 109 | Zeroize with media scrub |
| `system_zeroize_example.yml` | 112–113 | Full zeroize example via console server |

### Use Junos Snapshot Administrator in Python (JSNAPy) in Ansible Playbooks
*Chapter 5 — Pages 115–145*

| Playbook | Page | Description |
|---|---|---|
| `jsnapy_snap_pre_config_file.yml` | 119 | Pre-snapshot using config_file |
| `jsnapy_snap_pre_test_files.yml` | 119–120 | Pre-snapshot using test_files list |
| `jsnapy_snap_pre.yml` | 121–122 | Pre-snapshot with logfile |
| `jsnapy_snap_post.yml` | 122 | Post-snapshot with logfile |
| `jsnapy_check.yml` | 122–123 | Compare PRE and POST snapshots |
| `jsnapy_snapcheck.yml` | 124 | Snapshot and immediately evaluate |
| `jsnapy_snapcheck_dest_dir.yml` | 128 | Snapcheck with dest_dir for failed tests |
| `jsnapy_bgp_example.yml` | 139–141 | Full BGP config + JSNAPy verify example |

### Use Ansible to Retrieve or Compare Junos OS Configurations
*Chapter 6 — Pages 148–160*

| Playbook | Page | Description |
|---|---|---|
| `retrieve_committed.yml` | 149–150 | Retrieve committed configuration |
| `retrieve_candidate.yml` | 150 | Retrieve candidate configuration |
| `retrieve_filter_interfaces_protocols.yml` | 150–151 | Filter: interfaces + protocols |
| `retrieve_filter_specific_interface.yml` | 151–152 | Filter: specific interface |
| `retrieve_filter_system_services.yml` | 152 | Filter: system/services |
| `retrieve_format_xml.yml` | 153 | Retrieve in XML format |
| `retrieve_openconfig.yml` | 154–155 | Retrieve OpenConfig configuration |
| `retrieve_dest_dir.yml` | 156–157 | Save config to dest_dir |
| `retrieve_dest.yml` | 157–158 | Save config to dest with hostname |
| `compare_to_rollback.yml` | 158–159 | Compare active to rollback config |

### Use Ansible to Configure Junos Devices
*Chapter 6 — Pages 160–189*

| Playbook | Page | Description |
|---|---|---|
| `config_private_mode.yml` | 163–164 | Configure using private mode |
| `config_ephemeral_default.yml` | 165 | Configure ephemeral database |
| `config_load_set_strings.yml` | 168 | Load set-format strings |
| `config_load_text_strings.yml` | 168–169 | Load text-format strings |
| `config_load_local_file.yml` | 170 | Load from local file (src) |
| `config_load_remote_file.yml` | 170–171 | Load from remote file (url) |
| `config_load_jinja2.yml` | 173 | Load from Jinja2 template |
| `config_rescue.yml` | 174–175 | Revert to rescue configuration |
| `config_rollback.yml` | 175–176 | Roll back to previous configuration |
| `config_commit_confirmed.yml` | 179–180 | Commit with confirmation window |
| `config_ignore_warning_all.yml` | 180–181 | Suppress all warnings |
| `config_ignore_warning_specific.yml` | 181 | Suppress specific warnings |
| `config_example.yml` | 185 | Full configure example with file_copy |

---

## Authentication Quick Reference

| Method | Playbook |
|---|---|
| SSH keys (default location) | Any playbook without explicit credentials |
| Interactive prompt | `auth_password_prompt.yml` |
| `--ask-pass` CLI flag | `auth_ask_pass.yml` |
| Ansible Vault | `auth_vault.yml` |
| Vault + console server | `auth_console_server_vault.yml` |

---

## Connection Types

| Setting | Description |
|---|---|
| `connection: local` | Default. A new NETCONF session is opened per task. |
| `connection: juniper.device.pyez` | Persistent. One shared session for all tasks in the play. Authentication parameters must be defined in `vars:`. |
