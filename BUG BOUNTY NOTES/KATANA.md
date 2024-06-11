
**Setting the scan depth:**

```
katana scan -u target.com --depth 3
```

```
katana scan -u target.com --user-agent "User-Agent:Hackerone(hidalg0d)"
```

```
katana scan -u target.com -p xss,sql
```


```
katana -list {domains.txt} -d 5 -jc -rate-limit 4 | grep ".js$"  | uniq | sort
```

## SECRETFINDER + KATANA


```
cat {jsfilesgottenfromkatana.txt} | while read url; do python3
SecretFinder/SecretFinder.py  -i $url -o cli; done
```

