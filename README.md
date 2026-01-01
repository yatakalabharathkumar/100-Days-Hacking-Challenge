## 100 Days Hacking Challenge – Day 5

"One of the most overlooked phases in Reconnaissance is Virtual Host Discovery (or Reverse IP Lookup).

In modern cloud and shared hosting environments, a single public IP address rarely maps to just one domain. It usually serves content for dozens, sometimes hundreds, of different domains (Virtual Hosts).

Why is this critical for a pentester?

Scope Expansion: It reveals other assets owned by the target that you might have missed with subdomain enumeration.

Weakest Link: It identifies third-party sites hosted on the same server. If Target.com is secure but hosted on a shared cPanel server with Vulnerable-Wordpress-Blog.com, an attacker can exploit the blog to gain a shell on the server.

Tools used:

Bing ip: operator (e.g., ip:x.x.x.x)

HackerTarget API

Command line: host -t PTR <IP> (Reverse DNS, though less effective for virtual hosts)

Today's lesson: Always check the neighborhood."

