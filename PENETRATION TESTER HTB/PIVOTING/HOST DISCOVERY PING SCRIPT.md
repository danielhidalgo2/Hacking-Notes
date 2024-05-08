#!/bin/bash

network="10.0.0."

for ((i=1; i<=255; i++))
do
    ip="$network$i"
    # Realizar ping a la dirección IP
    ping -c 1 "$ip" >/dev/null 2>&1
    # Comprobar el código de salida del ping
    if [ $? -eq 0 ]; then
        echo "Host activo: $ip"
    fi
done
