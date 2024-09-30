# 

## Overview of the Vulnerability

HTTP request smuggling is a vulnerability that occurs due to the discrepancies between the way two or more servers interprets a sequence of requests, such as there the servers using different mechanisms to determine where the boundaries are between requests.

These misconfigurations can lead to a broad range of issues that result in an attacker bypassing security controls, taking over other user's accounts, or gaining unauthorized access to sensitive content.

## Business Impact

Depending on the type of misconfiguration found in the server, exposure or manipulation of data from within it could lead to financial loss and reputational damage for the business.

As an attacker, I could exploit a client-side desynchronization vulnerability on the target server at **<http://64.101.37.15>**. The server fails to handle the Content-Length of POST requests correctly, which leads to the following issues:

1.  **Issue Summary:** The server does not properly close the connection after handling POST requests and does not correctly process the request body if it is delayed. This flaw allows for the desynchronization of the connection, which can be exploited for HTTP request smuggling attacks.

2.  **Impact:** This vulnerability could potentially lead to various security issues such as Cross-Site Scripting (XSS), session fixation, or even unauthorized actions if exploited correctly. An attacker could trick a victim's browser into sending malicious payloads or manipulating requests in ways that the server does not anticipate, leading to unauthorized actions or data leakage.

3.  **Detailed Steps to Reproduce:**

    **Step 1:** Send a POST request to the path `/` with a delayed request body. Observe that the server does not close the connection and times out waiting for the request body.
    
```
    POST / HTTP/1.1
    Host: 64.101.37.15
    Accept-Encoding: gzip, deflate
    Accept: */*
    Accept-Language: en-US;q=0.9,en;q=0.8
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.5249.62 Safari/537.36
    Connection: keep-alive
    Cache-Control: max-age=0
    Content-Length: 348
    Content-Type: application/x-www-form-urlencoded
```



**Step 2:** Send a GET request immediately after the POST request. The server will interpret this as a new request due to the desynchronization.


```
GET /mgfhydz731?mgfhydz731=mgfhydz731 HTTP/1.1
    Host: 64.101.37.15
    Accept-Encoding: gzip, deflate
    Accept: */*
    Accept-Language: en-US;q=0.9,en;q=0.8
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.5249.62 Safari/537.36
    Connection: keep-alive
    Cache-Control: max-age=0
    X: tvzzzi8zuk
```
**Step 3:** Observe the server's responses. The server might return unexpected results, including unauthorized redirections or content leaks.

4.  **Proof of Concept:**

    Attached screenshots and network logs demonstrate the desynchronization in action and highlight how the server's responses differ when exploiting this vulnerability.