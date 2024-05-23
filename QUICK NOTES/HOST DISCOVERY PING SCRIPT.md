


```
#!/bin/bash

for host in $(seq 1 254); do
	timeout 1 bash -c "ping -c 1 20.20.20.$host &>/dev/null" && echo "[+] HOST - 20.20.20.$host"
done; wait
```

