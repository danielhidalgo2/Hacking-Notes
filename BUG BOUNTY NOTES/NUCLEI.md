

## BUGCROWD

```
nuclei -u https:// -t nuclei-templates/http/technologies/nginx/nginx-version.yaml -header 'User-Agent:Bugcrowd(hidalg0d)' 
```

## HACKERONE
```
nuclei -u https:// -t nuclei-templates/http/technologies/nginx/nginx-version.yaml -header 'User-Agent:Hackerone(hidalg0d)' 
```

```
nuclei -l list.txt -t /home/daniel/.local/nuclei-templates/http -severity low,medium -rate-limit 4  -header 'User-Agent:Bugcrowd(hidalg0d)' 
```


```
nuclei -u** [**http://testphp.vulnweb.com/**](http://testphp.vulnweb.com/) **-t nuclei-templates -tags xss

nuclei -u [**http://testphp.vulnweb.com/**](http://testphp.vulnweb.com/) -t nuclei-templates -author hackergautam

nuclei -u [**http://testphp.vulnweb.com/**](http://testphp.vulnweb.com/) -t nuclei-templates -severity low,medium,high,critical
```
Nuclei is simple to get up-and-running without having to read a lot of documentation. After installing the tool, it can be as simple as running (for a single target):

```bash
nuclei -u https://my.target.site
```


```
nuclei -l /path/to/list-of-targets.txt
```

```
subfinder -d targetdomain.com -silent | httpx | nuclei -t technologies/tech-detect.yaml
```

**Timeout Length (-timeout)**

We can set the amount of time before a connection attempt times-out using this option. The default value is 5 seconds, however we may want to reduce the time to complete the scan more quickly if we are scanning many hosts. Example:

```bash
nuclei -l list-of-targets.txt -timeout 1
```

Bash

**Number of Retries (-retries)**

By default, Nuclei won’t retry a failed connection attempt. Using the retry option, we can set the number of retries. Example:

```bash
nuclei -l list-of-targets.txt -retries 3
```

Bash

**Number of Errors (-mhe)**

The default setting for nuclei to abandon scanning a host due to errors is 30. We can increase or decrease this number using the max errors option. Example:

```bash
nuclei -l list-of-targets.txt -mhe 3
```

You can resume the scan from the last request with a command similar to the following:

```bash
nuclei -l targets-file.txt -resume /path/to/resume-file.cfg
```



```bash
subfinder -d example.com > urls.txt

httpx -l urls.txt -o livehosts.txt

katana -u livehosts.txt -o endpoints.txt

nuclei -l filtered_endpoints.txt -t ~/.local/nuclei-templates/vulnerabilities/ -tags xss,sqli,ssrf,redirect,lfi,rfi,path-traversal,idor,command-injection -rate-limit 4 
```