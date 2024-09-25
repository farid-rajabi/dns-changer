# DNS Changer [![GitHub Release](https://img.shields.io/github/v/release/farid-rajabi/dns-changer)](https://github.com/farid-rajabi/dns-changer/releases/latest)

[![GitHub License](https://img.shields.io/github/license/farid-rajabi/dns-changer)](https://github.com/farid-rajabi/dns-changer/blob/main/LICENSE)

A command-line application assisting with changing the global DNS addresses of your system.

**Available for ![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black).**

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
| 403 | 10.202.10.202 | 10.202.10.102 |
| Cisco Umbrella | 208.67.222.222 | 208.67.220.220 |
| Verisign | 64.6.64.6 | 64.6.65.6 |
| Electro | 78.157.42.101 | 78.157.42.100 |
| Radar Plus | 10.202.10.10 | 10.202.10.11 |

## Installation

1.  Run the following command to install *resolvconf*:

    ```sh
    sudo apt-get install resolvconf
    sudo apt-get install net-tools
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

3.  Put the *dns-changer* file into your *~/bin* directory. (If this directory does not exist, create it.)

4.  Run the following command to find the alias used for your router:

    ```sh
    iwconfig
    ```

5.  Open *~/bin/dns-changer* using a text editor and enter the alias after `alias=`.

> [!NOTE]
> Do NOT forget to surround the alias with double quotation marks. For example:
>
> ```
> alias="wlo1"
>```

6.  Log out or reboot to make the app available through your terminal.

7.  Run the following command to check whether the app is available or not:

    ```sh
    dns-changer --version
    ```

8.  (Optional) Install *[speedtest-cli](https://github.com/sivel/speedtest-cli)* to make the *speed-test* command available through the app:

```sh
pip install speedtest-cli
```

> [!TIP]
> Try `pip3` in case you do not have `pip` installed on your system.

## How to Use

Run this line to see all the commands:

```sh
dns-changer --help
```

The mostly used commands are as follows:

- **Check** the current DNS addresses: Run this line to see your global DNS:

    ```sh
    dns-changer check
    ```

- **Change** the DNS addresses: Run this line to see the list of DNS servers and their corresponding addresses:

    ```sh
    dns-changer list
    ```

    Run this line to set your new global DNS addresses:

    ```sh
    dns-changer change "server-name"
    ```

> [!NOTE]
> `server-name` is the full name of the server that is surrounded by brackets when it is listed using `dns-changer list`.

- **Flush** the current DNS addresses: Flush the global DNS addresses using the following command:

    ```sh
    dns-changer flush
    ```

- **Set** custom DNS server addresses: Set your desired DNS addresses using the `set` command:

    ```
    dns-changer set <add.ress.1> <add.ress.2>
    ```

- (Optional) **Speed test**: Run this command to measure your download/upload speed:

    ```sh
    dns-changer speed-test
    ```

## Disclaimer

The developer, [Farid Rajabi](https://github.com/farid-rajabi), is not responsible for security and stability of the DNS servers mentioned above which are available through this application, [DNS Changer](https://github.com/farid-rajabi/dns-changer). It is a work of compilation of available DNS server addresses which are freely accessible through the internet.
