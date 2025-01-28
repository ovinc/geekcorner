# SSH connection to other computers

## General

To connect to remote machines (local machines, servers, etc.), use the following general expression:
```bash
ssh username@address
```
where `address` can be a hostname (machine name) or an IP address.

To quit the remote session
```bash
logout
```

## MacOS

The hostname / IP address / session name of the machine can be found in *Settings/Sharing*, in the "Remote Login" tab.

Typically, the hostname in the local network is the name of the machine with spaces replaced by dashes, with `.local` added in the end; e.g. to connect to the *John Martin* session of *My MacBook*
```bash
ssh john-martin@my-macbook.local
```
(upper/lower case does not matter here.)

*NOTE*: the possibility of remote access must be activated in *Settings/Sharing* to be able to connect remotely. Sometimes, this means allowing to anyone, or just to administrators.


## Custom hostnames

Custom hostnames are possible with several methods :


- Using the SSH Configuration File at `~/.ssh/config`, by adding an entry:
    ```
    Host local_computer_hostname
        HostName 192.168.1.104
        User username
    ```
    Then it's possible to SSH with
    :
    ```bash
    ssh local_computer_hostname
    ```


- Editing the `/etc/hosts` file on both the local and remote computers to include the IP and hostname of the local computer, e.g.
    ```bash
    192.168.1.104  local_computer_hostname
    ```
    Then it's possible to SSH with
    ```bash
    ssh username@local_computer_hostname
    ```

