# Connection Master
A command line remote server connection and management tool

# Installation
```
$ git clone https://github.com/nathansmerrill/connectionmaster ~/connectionmaster
$ pip install --user -r ~/connectionmaster/requirements.txt
$ echo alias cm='python3 ~/connectionmaster/connectionmaster.py' > ~/.bashrc
```
Set `CONFIG_FILE` in `connectionmaster.py` to your config file location. The default is `/home/nathan/.cmrc.yaml`

# Usage
There are long and one letter forms for every command
```
$ cm connect myServer
$ cm c myServer
$ cm execute mySecondServer "echo hi > test.txt"
$ cm x mySecondServer "echo hi > test.txt"
$ cm ping myThirdServer
$ cm p myThirdServer
$ cm edit
$ cm e
```

# Config file
```yaml
myServer:
    ip: 'xxx.xxx.xxx.xxx'
    user: 'myUser'

# The jump option takes the server to jump ssh through
mySecondServer:
    ip: 'yyy.yyy.yyy.yyy'
    port: '2000'
    key: 'mySecondServerKey'
    jump: 'myServer'

# The ip isn't needed when you specify a full command but is needed to ping the server
myThirdServer:
    ip: 'zzz.zzz.zzz.zzz'
    command: 'vncviewer zzz.zzz.zzz.zzz:0'
    justRunCommand: True

```

# Config values
| Value | Meaning | Default |
| --- | --- | --- |
| `command` | The command to run | `ssh` |
| `user` | The user to log in as | The current user |
| `ip` | The IP to connect to | `localhost` |
| `port` | The por to connect to | `22` |
| `key` | The ssh key to use | No key |
| `jump` | A server to jump ssh through | Nothing |
| `justRunCommand` | Just runs `command` without adding ip, port, etc | `False` |