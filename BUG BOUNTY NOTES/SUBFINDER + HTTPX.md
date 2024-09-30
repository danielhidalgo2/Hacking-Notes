
```
subfinder -d vulnweb.com | httpx -title -status-code -tech-detect -follow-redirects -o alive.txt
```

```
subfinder -all -d <domain-name> -o <output-filename1> -silent
```

```
subfinder -d XXX.com -o actives.txt -nW

```

## AMASs + HTTPX

```
amass enum -brute -d example.com '/home/user/.config/amass/config.ini' | httpx -title -tech-detect -status-code -ip -p 66,80,81,443,445,457,1080,1100,1241,1352,1433,1434,1521,1944,2301,3000,3128,3306,4000,4001,4002,4100,5000,5432,5800,5801,5802,6082,6346,6347,7001,7002,8080,8443,8888,30821

```