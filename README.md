# DNS Changer

[![GitHub Release](https://img.shields.io/github/v/release/farid-rajabi/dns-changer)](https://github.com/farid-rajabi/dns-changer/releases/latest)
[![GitHub License](https://img.shields.io/github/license/farid-rajabi/dns-changer)](https://github.com/farid-rajabi/dns-changer/blob/main/LICENSE)

A command-line application assisting with changing the global DNS of your system.

**Available for Linux.**

Available servers:

| Server Name | Address 1 | Address 2 |
| --- | --- | --- |
| Google | 8.8.8.8 | 8.8.4.4 |
| Yandex Basic | 77.88.8.8 | 77.88.8.1 |
| Yandex Safe | 77.88.8.88 | 77.88.8.2 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 |
| OpenDNS | 208.67.222.222 | 208.67.220.220 |
| OpenDNS FamilyShield | 208.67.222.123 | 208.67.220.123 | 
| Comodo Secure | 8.26.56.26 | 8.20.247.20 |
| Comodo Secure Internet Gateway | 8.26.56.10 | 8.20.247.10 |
| Quad9 | 9.9.9.9 | 149.112.112.112 |
| Norton ConnectSafe | 199.85.126.10 | 199.85.127.10 |
| Level3 | 209.244.0.3 | 209.244.0.4 |
| Shecan | 178.22.122.100 | 185.51.200.2 |

## Installation

### Main Steps

1.  Run the following command to install *resolvconf*:

    ```sh
    sudo apt-get install resolvconf
    ```

2.  Check the service status using the following command:

    ```sh
    sudo systemctl status resolvconf.service
    ```

    If the output looks like the example below, it is active.

    ```
    $ sudo systemctl status resolvconf.service
    ● resolvconf.service - Nameserver information manager
        Loaded: loaded (/lib/systemd/system/resolvconf.service; enabled; vendor pr>
        Active: active (exited) since Tue 2024-09-03 13:17:57 +0330; 5h 52min ago
        Docs: man:resolvconf(8)
        Process: 285 ExecStart=/sbin/resolvconf --enable-updates (code=exited, stat>
    Main PID: 285 (code=exited, status=0/SUCCESS)
            CPU: 4ms
    ```

    Otherwise, run the following commands to activate the service:

    ```sh
    sudo systemctl start resolvconf.service
    sudo systemctl enable resolvconf.service
    sudo systemctl status resolvconf.service
    ```

3.  Put the *dns-changer* file into your *~/bin* directory.

4.  Log out or reboot to make the app available through your terminal.

5.  Run the following command to check whether the app is available or not:

    ```sh
    dns-changer --version
    ```

### Optional Step

6.  Install *[speedtest-cli](https://github.com/sivel/speedtest-cli)* to make the *speed-test* command available through the app:

```sh
pip install speedtest-cli
```

## How to Use

Run this line to see all the commands:

```sh
dns-changer --help
```

The mostly used commands are as follows:

### Check the DNS

Run this line to see your global DNS:

```sh
dns-changer check
```

### Change the DNS

Run this line to see the list of servers and their IPv4 addresses:

```sh
dns-changer list
```

Run this line to set your global DNS:

```sh
dns-changer change "server-name"
```

> [!NOTE]
> `server-name` is the full name of the server surrounded by brackets.

### Add Custom Servers

The *dns-changer* file can be easily opened using a text editor. Feel free to add more DNS servers in the following format to the `dns_servers` variable.

```
<empty-line>
[<server-name>]
<add.ress.1>
<add.ress.2>
```

### Speed Test (Optional)

Run this line to see your download/upload speed:

```sh
dns-changer speed-test
```
