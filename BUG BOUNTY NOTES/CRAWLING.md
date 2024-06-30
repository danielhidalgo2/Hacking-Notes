
```
curl -sL http://index.commoncrawl.org | grep 'href="/CC'  |  awk -F'"' '{print $2}' | xargs -n1 -I{} curl -sL http://index.commoncrawl.org{}-index?url=http://yahoo.com* |  awk -F'"url":\ "' '{print $2}' | cut -d'"' -f1 | sort -u | tee domain.txt
```

