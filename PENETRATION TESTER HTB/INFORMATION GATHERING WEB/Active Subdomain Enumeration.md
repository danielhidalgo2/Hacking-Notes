
## Gobuster

Gobuster is a tool that we can use to perform subdomain enumeration. It is especially interesting for us the patterns options as we have learned some naming conventions from the passive information gathering we can use to discover new subdomains following the same pattern.

We can use a wordlist from [Seclists](https://github.com/danielmiessler/SecLists) repository along with `gobuster` if we are looking for words in patterns instead of numbers. Remember that during our passive subdomain enumeration activities, we found a pattern `lert-api-shv-{NUMBER}-sin6.facebook.com`. We can use this pattern to discover additional subdomains. The first step will be to create a patterns.txt file with the patterns previously discovered, for example:

#### GoBuster - patterns.txt

  Active Subdomain Enumeration

```shell-session
lert-api-shv-{GOBUSTER}-sin6
atlas-pp-shv-{GOBUSTER}-sin6
```

The next step will be to launch `gobuster` using the `dns` module, specifying the following options:

- `dns`: Launch the DNS module
- `-q`: Don't print the banner and other noise.
- `-r`: Use custom DNS server
- `-d`: A target domain name
- `-p`: Path to the patterns file
- `-w`: Path to the wordlist
- `-o`: Output file

In our case, this will be the command.

#### Gobuster - DNS

  Active Subdomain Enumeration

```shell-session
hidalg0dd@htb[/htb]$ export TARGET="facebook.com"
hidalg0dd@htb[/htb]$ export NS="d.ns.facebook.com"
hidalg0dd@htb[/htb]$ export WORDLIST="numbers.txt"
hidalg0dd@htb[/htb]$ gobuster dns -q -r "${NS}" -d "${TARGET}" -w "${WORDLIST}" -p ./patterns.txt -o "gobuster_${TARGET}.txt"

Found: lert-api-shv-01-sin6.facebook.com
Found: atlas-pp-shv-01-sin6.facebook.com
Found: atlas-pp-shv-02-sin6.facebook.com
Found: atlas-pp-shv-03-sin6.facebook.com
Found: lert-api-shv-03-sin6.facebook.com
Found: lert-api-shv-02-sin6.facebook.com
Found: lert-api-shv-04-sin6.facebook.com
```

