#!/bin/bash

for host in $(seq 1 254); do
        timeout 1 bash -c "echo '' > /dev/tcp/30.30.30.$host/80 &>/dev/null" && echo "[+] HOST - 30.30.30.$host"
done; wait