# Intro to Web Proxies

Web proxies are specialized tools that cna be seup between a device and a back-end server to capture and view all the web requests being sent.

Covering `Burp Suite` and `Zap`

## Burp Suite

Most common web proxy for web penetration testing.

## ZAP

OWASP Zed Attack Proxy open-source project from Open Web Application Security Project (OWASP).

## Proxychains

Proxychains adds a proxy to any command-line tool and is hence the simplest and easiest method to route web traffic of command-line tools through our web proxies

`/etc/proxychains.conf`

```sh
#socks4         127.0.0.1 9050
http 127.0.0.1 8080
```

uncomment `quiet_mode`

### Using with commands

`proxychains curl http://SERVER_IP:PORT`

`nmap --proxies http://127.0.0.1:8080 SERVER_IP -pPORT -Pn -sC`

In msfconsole

`set PROXIES HTTP:127.0.0.1:8080`

## Burp Intruder

Burp's web fuzzer is called Burp Intruder, and can be used to fuzz pages, directories, sub-domains, parameters, parameters values, and many other things. Though it is much more advanced than most CLI-based web fuzzing tools, the free Burp Community version is throttled at a speed of 1 request per second, making it extremely slow compared to CLI-based web fuzzing tools, which can usually read up to 10k requests per second.

Send to Intruder `CTRL+I`

We can then go to Intruder by clicking on its tab or with the shortcut [CTRL+SHIFT+I]

https://portswigger.net/burp/documentation/desktop/tools/intruder/configure-attack/positions#attack-type


## Zap Fuzzer

Set ZAP Mode to Attack for Fuzzing