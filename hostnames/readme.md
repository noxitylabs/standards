
# Hostname Identification Standard
An open and standardized way to name and identify your devices like network equipment, network tools, hypervisors, looking glasses and PTRs.

## Syntax
### Server Hardware
To identify server nodes like VPS hosts, bare-metal, storage or GPU servers, use the following format:
```
{NODE}-{PURPOSE}-[FACILITY]-[CITY]-[COUNTRY].{DOMAIN}.{TLD}
```

|     Tag      | Required | Description                                                                                              |
|:------------:|----------|----------------------------------------------------------------------------------------------------------|
| `{NODE-ID}`     | ✅        | Unique node identifier which must be number. See [Numbering Segment Rules](#numbering-segment-rules).                                              |                                                       |
| `{PURPOSE}`  | ✅        | Purpose of the node. Examples: `vps`, `bm`, `gpu`, `ceph`, `db`, etc. See [Purpose Tags](#purpose-tags). |
| `{FACILITY}` | ✅ | Facility name with ID, helpful when multiple locations exist within the same city. If there is just one facility do not add numbers. When adding numbers follow [Numbering Segment Rules](#numbering-segment-rules) and refer to [Facility Tags](#facility-tags) for all available facilities.                |
| `{CITY}`     | ✅ | IATA airport code of the closest international airport for that city. If there are multiple, use the largest airport's code.                                               |
| `[COUNTRY}`  | ✅ | 2-letter country code according to ISO 3166-1 alpha-2                                                |
| `{DOMAIN}`   | ✅        | Your domain name.                                                                                         |
| `{TLD}`      | ✅        | TLD for your domain.                                                    |

**Examples**:  
`48-vps-nikhef-ams-nl.nodeid.net`  
`1-vpn-fri-lju-si.nodeid.net`  
`32-game-equinix13-iad-us.nodeid.net`  

---
### Numbering Segment Rules

Use the following format for numbered tags:

- **01–09** → Use leading zero for single digits.
- **10, 100, 1000, ...** → No leading zeros for double digits and beyond.

| Example Input | Formatted Tag |
|---------------|----------------|
| 1             | 01             |
| 9             | 09             |
| 10            | 10             |
| 100           | 100            |
| 1000          | 1000           |


### Purpose Tags
Standardized values for `{PURPOSE}` in server hardware naming:

| Tag   | Description               |
|-------|---------------------------|
| `api` | API Node                  |
| `db`  | Database Server           |
| `game`| Game Hosting Hypervisor   |
| `lb`  | Load Balancer             |
| `mbm` | Managed Bare Metal        |
| `mx`  | Mail Server               |
| `ssh` | SSH Box Server            |
| `vm`  | Virtual Machine Hypervisor|
| `vpn` | VPN Server                |
| `fr-{tag}` | Free-tier service (e.g., free hosting for students, trial servers). Combine with another tag from this list to specify the resource type.                |
| `vps` | Internal VPS Server |
| `web` | Web Hosting Hypervisor    |

### Facility Tags
Use this table to document and standardize your facility tags:

| Tag         | Description                       | Location               |
|-------------|-----------------------------------|------------------------|
| `nikhef`    | Nikhef Data Center                | Amsterdam, Netherlands |
| `fri`       | Faculty of Computer Science       | Ljubljana, Slovenia    |

You can expand this list as needed. Use a consistent naming convention when adding new facilities, especially when numbering them (e.g., `dc01`, `dc02`).

---
### Looking Glasses
Simplified hostname format for Looking Glass instances:

```
lg.{CITY}.{DOMAIN}.{TLD}
```

| Tag       | Required | Description                         |
|:----------|----------|-------------------------------------|
| `{CITY}`  | ✅        | IATA airport code of the closest international airport for that city. If there are multiple, use the largest airport's code. |
| `{DOMAIN}`| ✅        | Main domain name of the company                         |
| `{TLD}`   | ✅        | TLD of the company main domain     |

**Examples**:  
`lg.ams.noxity.io`  - Amsterdam, Netherlands
`lg.mel.noxity.io`  - Melbourne, Australia
`lg.lax.noxity.io`- Los Angeles, United States

> ⚠️ This hostname must point to a public IP within network. Do **not** put a Looking Glass behind a reverse proxy like Cloudflare.

---
### DNS
To do this naming properly, it is expected to properly set up DNS, meaning that a hostname must end up with A or AAAA records to the IP of the device.  
Vice versa it is recommended to maintain a reverse PTR record from IP address to the hostname.
