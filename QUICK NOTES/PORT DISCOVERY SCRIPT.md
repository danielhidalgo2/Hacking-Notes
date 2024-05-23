(ESTE SCRIPT ESCANEA LOS 100 PRIMEROS PUERTOS)

#!/bin/bash

for i in $(seq 1 100); do bash -c "echo '' > /dev/tcp/20.20.20.3/$i" 2>/dev/null && echo "Este puerto esta abierto: $i"; 
done
