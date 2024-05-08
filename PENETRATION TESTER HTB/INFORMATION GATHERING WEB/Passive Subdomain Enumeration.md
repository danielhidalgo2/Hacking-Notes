## Certificates

Another interesting source of information we can use to extract subdomains is SSL/TLS certificates. The main reason is Certificate Transparency (CT), a project that requires every SSL/TLS certificate issued by a Certificate Authority (CA) to be published in a publicly accessible log.

We will learn how to examine CT logs to discover additional domain names and subdomains for a target organization using two primary resources:

- [https://censys.io](https://censys.io/)
    
- [https://crt.sh](https://crt.sh/)
    

We can navigate to https://search.censys.io/certificates or https://crt.sh and introduce the domain name of our target organization to start discovering new subdomains.

![image](https://academy.hackthebox.com/storage/modules/144/censys_facebook.png)

   

![](https://academy.hackthebox.com/storage/modules/144/crt_facebook.png)

#### TheHarvester

[TheHarvester](https://github.com/laramies/theHarvester) is a simple-to-use yet powerful and effective tool for early-stage penetration testing and red team engagements. We can use it to gather information to help identify a company's attack surface. The tool collects `emails`, `names`, `subdomains`, `IP addresses`, and `URLs` from various public data sources for passive information gathering. For now, we will use the following modules:

|||
|---|---|
|[Baidu](http://www.baidu.com/)|Baidu search engine.|
|`Bufferoverun`|Uses data from Rapid7's Project Sonar - [www.rapid7.com/research/project-sonar/](http://www.rapid7.com/research/project-sonar/)|
|[Crtsh](https://crt.sh/)|Comodo Certificate search.|
|[Hackertarget](https://hackertarget.com/)|Online vulnerability scanners and network intelligence to help organizations.|
|`Otx`|AlienVault Open Threat Exchange - [https://otx.alienvault.com](https://otx.alienvault.com/)|
|[Rapiddns](https://rapiddns.io/)|DNS query tool, which makes querying subdomains or sites using the same IP easy.|
|[Sublist3r](https://github.com/aboul3la/Sublist3r)|Fast subdomains enumeration tool for penetration testers|
|[Threatcrowd](http://www.threatcrowd.org/)|Open source threat intelligence.|
|[Threatminer](https://www.threatminer.org/)|Data mining for threat intelligence.|
|`Trello`|Search Trello boards (Uses Google search)|
|[Urlscan](https://urlscan.io/)|A sandbox for the web that is a URL and website scanner.|
|`Vhost`|Bing virtual hosts search.|
|[Virustotal](https://www.virustotal.com/gui/home/search)|Domain search.|
|[Zoomeye](https://www.zoomeye.org/)|A Chinese version of Shodan.|

[Netcraft](https://www.netcraft.com/) can offer us information about the servers without even interacting with them, and this is something valuable from a passive information gathering point of view. We can use the service by visiting `https://sitereport.netcraft.com` and entering the target domain.

   

![](https://academy.hackthebox.com/storage/modules/144/netcraft_facebook.png)

Some interesting details we can observe from the report are:

|||
|---|---|
|`Background`|General information about the domain, including the date it was first seen by Netcraft crawlers.|
|`Network`|Information about the netblock owner, hosting company, nameservers, etc.|
|`Hosting history`|Latest IPs used, webserver, and target OS.|

We need to pay special attention to the latest IPs used. Sometimes we can spot the actual IP address from the webserver before it was placed behind a load balancer, web application firewall, or IDS, allowing us to connect directly to it if the configuration allows it. This kind of technology could interfere with or alter our future testing activities.

---

## Wayback Machine

The [Internet Archive](https://en.wikipedia.org/wiki/Internet_Archive) is an American digital library that provides free public access to digitalized materials, including websites, collected automatically via its web crawlers.

We can access several versions of these websites using the [Wayback Machine](http://web.archive.org/) to find old versions that may have interesting comments in the source code or files that should not be there. This tool can be used to find older versions of a website at a point in time. Let's take a website running WordPress, for example. We may not find anything interesting while assessing it using manual methods and automated tools, so we search for it using Wayback Machine and find a version that utilizes a specific (now vulnerable) plugin. Heading back to the current version of the site, we find that the plugin was not removed properly and can still be accessed via the `wp-content` directory. We can then utilize it to gain remote code execution on the host and a nice bounty.

![image](https://academy.hackthebox.com/storage/modules/144/wayback1.png)

We can check one of the first versions of `facebook.com` captured on December 1, 2005, which is interesting, perhaps gives us a sense of nostalgia but is also extremely useful for us as security researchers.

   

![](https://academy.hackthebox.com/storage/modules/144/wayback2.png)

We can also use the tool [waybackurls](https://github.com/tomnomnom/waybackurls) to inspect URLs saved by Wayback Machine and look for specific keywords. Provided we have `Go` set up correctly on our host, we can install the tool as follows: