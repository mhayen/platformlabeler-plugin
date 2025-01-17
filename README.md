# Platform Labeler Plugin

Adds labels to Jenkins agents based on characteristics of the operating system running the agent.
Labels commonly include operating system name, version, and architecture.

| Platform                   | Operating System   | Version        | Architecture |
| -------------------------- | ------------------ | -------------- | ------------ |
| Alpine                     | `Alpine`           | `3.9.4`        | `amd64`      |
| Amazon Linux               | `AmazonAMI`        | `2018.03`      | `amd64`      |
| Amazon Linux 2             | `Amazon`           | `2`            | `amd64`      |
| CentOS 6                   | `CentOS`           | `6.10`         | `amd64`      |
| CentOS 7                   | `CentOS`           | `7.7.1908`     | `amd64`      |
| Debian 9                   | `Debian`           | `9.11`         | `amd64`      |
| Debian 10                  | `Debian`           | `10`           | `aarch64`    |
| Debian 10                  | `Debian`           | `10`           | `amd64`      |
| Debian testing             | `Debian`           | `testing`      | `amd64`      |
| FreeBSD 11                 | `freebsd`          | `11.1-STABLE`  | `amd64`      |
| FreeBSD 12                 | `freebsd`          | `12.0-RELEASE` | `amd64`      |
| Oracle Linux 6             | `OracleServer`     | `6.10`         | `amd64`      |
| Oracle Linux 7             | `OracleServer`     | `7.6`          | `amd64`      |
| Oracle Linux 8             | `OracleServer`     | `8.0`          | `amd64`      |
| Red Hat Enterprise Linux 7 | `RedHatEnterprise` | `7.7`          | `amd64`      |
| Red Hat Enterprise Linux 8 | `RedHatEnterprise` | `8.0`          | `amd64`      |
| Scientific 6.10            | `Scientific`       | `6.10`         | `amd64`      |
| Scientific 7.7             | `Scientific`       | `7.7`          | `amd64`      |
| SLES 11.3                  | `SUSE`             | `11.3`         | `amd64`      |
| SLES 12.1                  | `SUSE`             | `12.1`         | `amd64`      |
| SLES 12.2                  | `SUSE`             | `12.2`         | `amd64`      |
| SLES 15                    | `SUSE`             | `15`           | `amd64`      |
| Ubuntu 14                  | `Ubuntu`           | `14.04`        | `amd64`      |
| Ubuntu 16                  | `Ubuntu`           | `16.04`        | `amd64`      |
| Ubuntu 18                  | `Ubuntu`           | `18.04`        | `amd64`      |
| Windows 10                 | `windows`          | `10.0`         | `amd64`      |

On Linux computers, the plugin uses the output of the [`lsb_release`](https://linux.die.net/man/1/lsb_release) command.
If `lsb_release` is not installed, labels on Linux agents will be guessed based on values in /etc/os-release.
Redhat and Scientific agents have another fallback based on /etc/redhat-release.
Agents with an older version of SuSE will fallback to /etc/SuSE-release. Older versions of this plugin might return "sles" or "SUSE LINUX" as OS name.
This has been unified to "SUSE" as this is the lsb_release ID since SLES 12 SP2.

When /etc/os-release is used, less detailed labels are provided.
For example:

| Platform                   | Operating System   | Version        | Architecture |
| -------------------------- | ------------------ | -------------- | ------------ |
| CentOS 7                   | `CentOS`           | `7`            | `amd64`      |

One can configure globally and per agent which labels should be generated.
To define the labels for an agent, just check 'Automatic Platform Labels' in the Node Properties section and select the labels you want to have.
