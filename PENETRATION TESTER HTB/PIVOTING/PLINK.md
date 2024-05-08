
[Plink](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html), short for PuTTY Link, is a Windows command-line SSH tool that comes as a part of the PuTTY package when installed. Similar to SSH, Plink can also be used to create dynamic port forwards and SOCKS proxies. Before the Fall of [2018](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_overview), Windows did not have a native ssh client included, so users would have to install their own. The tool of choice for many a sysadmin who needed to connect to other hosts was [PuTTY](https://www.putty.org/).

```cmd-session
plink -ssh -D 9050 ubuntu@10.129.15.50
```

