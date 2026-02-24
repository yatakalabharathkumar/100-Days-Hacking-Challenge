## 🗓️ Day 59/100 – SSRF Introduction & Basic Labs

**Focus:** Learning what Server-Side Request Forgery is and solving basic SSRF labs.

### 🌐 What is SSRF?

Server-Side Request Forgery (SSRF) happens when:

- An application sends HTTP requests based on a **user-supplied URL or host**, and
- It does not properly validate or restrict where that server-side request can go.

As a result, an attacker can:
- Make the server send requests to internal services or external targets.
- Potentially read responses that would normally be inaccessible from the internet.

### 🧪 Lab Concepts

Example pattern:

```http
POST /check-stock HTTP/1.1
Host: vulnerable-app.com

stockUrl=http://internal-api/stock/item/1
If stockUrl is user-controlled and not validated, it can be changed to:

http://localhost/admin

http://192.168.0.10:8080/

Cloud metadata URL such as http://169.254.169.254/latest/meta-data/

Basic labs showed:

How to modify parameters to scan internal IP ranges.

How to access a local admin panel through a stock check or similar feature.

In some scenarios, how the server’s response reveals internal information directly.

🛡️ Defensive Ideas (Preview)
Use allowlists of permitted domains/paths for server-side requests.

Block requests to internal ranges and metadata endpoints at the code and network levels.

Avoid exposing raw responses from internal services back to the user.

Day 59 Summary:
Today’s labs showed that if a server will fetch arbitrary URLs for you, it can become an unwilling proxy into its own internal network.
