
https://github.com/danielhidalgo2/JSEXPOSURES

```bash
katana -u livehosts.txt -d 3 -silent -o endpoints.txt


grep "\.js" endpoints.txt > js_endpoints.txt


cat domains.txt | katana | grep js | httpx -mc 200 | tee js.txt

python exposures.py
```


