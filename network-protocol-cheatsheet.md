# Network Protocols & Email Cheatsheet

> Beginner-friendly reference for the protocols DevOps engineers use most: web traffic, encryption, remote access, file transfer, DNS, and email delivery.

## How To Use This Sheet

If you are fresh to networking, start in this order:

1. OSI Model
2. DNS
3. HTTP and HTTPS
4. TLS
5. SSH
6. SMTP, IMAP, and POP3S
7. SPF, DKIM, and DMARC

---

## 1. OSI Model (Quick Ref)

The OSI model explains how data moves from one computer to another over a network.

### Easy Memory Trick

`All People Seem To Need Data Processing`

Or reverse it:

`Please Do Not Throw Sausage Pizza Away`

### OSI Layers

| Layer | Name | What It Does | Example |
|---|---|---|---|
| 7 | Application | User-facing network apps | HTTP, HTTPS, DNS, SMTP |
| 6 | Presentation | Encryption and formatting | TLS |
| 5 | Session | Keeps conversations alive | Login session |
| 4 | Transport | Reliable delivery and ports | TCP, UDP |
| 3 | Network | Routing between networks | IP addresses |
| 2 | Data Link | Local network communication | MAC addresses, switches |
| 1 | Physical | Cables and signals | Ethernet, Wi-Fi |

### Real Life Flow

```text
Browser
-> HTTP/HTTPS
-> TCP/IP
-> Network card
-> Internet
-> Server
```

### DevOps Focus

| Concept | Why It Matters |
|---|---|
| TCP/UDP | App connectivity |
| DNS | Find servers by name |
| HTTP/HTTPS | Web apps and APIs |
| TLS | Secure traffic |
| IP and routing | Cloud and server networking |
| SSH | Remote server access |
| Ports | Open the right services |

---

## 2. HTTP / HTTPS

### What Is HTTP?

HTTP is the protocol for browser-to-server communication.

Example:

```text
Browser <-> Web server
```

### Common HTTP Methods

| Method | Purpose |
|---|---|
| GET | Fetch data |
| POST | Send or create data |
| PUT | Update or replace data |
| DELETE | Remove data |

### HTTP Status Codes

| Code | Meaning |
|---|---|
| 200 | Success |
| 301 | Redirect |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not found |
| 500 | Internal server error |
| 502 | Bad gateway |
| 503 | Service unavailable |

### What Is HTTPS?

HTTPS is HTTP plus TLS encryption.

| Feature | HTTP | HTTPS |
|---|---|---|
| Secure | No | Yes |
| Encryption | No | TLS |
| Default port | 80 | 443 |
| Used today | Rare | Everywhere |

### Useful Commands

```bash
curl https://example.com
curl -I https://example.com
curl -o /dev/null -w "%{http_code}" https://example.com
nc -zv example.com 443
```

### DevOps Use Cases

- Nginx reverse proxy
- API testing with curl or Postman
- Load balancing web traffic
- Redirecting HTTP to HTTPS

---

## 3. SSL / TLS

### What Is TLS?

TLS encrypts network communication. SSL is the older name.

### Why It Matters

Without TLS, data can be read in transit.
With TLS, data is encrypted.

### TLS Handshake

```text
1. Client connects
2. Server sends certificate
3. Client verifies certificate
4. Keys are created
5. Encrypted communication starts
```

### Important Terms

| Term | Meaning |
|---|---|
| Certificate | Proves the server identity |
| CA | Certificate Authority that issues certs |
| Private key | Secret key kept on the server |
| Public key | Key shared with clients |
| SNI | Lets one IP host multiple certificates |

### Common TLS Ports

| Service | Port |
|---|---|
| HTTPS | 443 |
| SMTPS | 465 |
| IMAPS | 993 |
| POP3S | 995 |
| SSH | 22 |

### Useful Commands

```bash
openssl s_client -connect example.com:443
curl -v https://example.com
```

### DevOps Responsibilities

- Install certificates
- Renew certificates before expiry
- Configure TLS in Nginx or Apache
- Redirect HTTP traffic to HTTPS
- Debug certificate errors

---

## 4. SSH

### What Is SSH?

SSH is used to securely log into remote Linux servers.

### Basic Command

```bash
ssh user@server-ip
```

Example:

```bash
ssh ubuntu@10.0.0.5
```

### Authentication Types

| Type | Description |
|---|---|
| Password auth | Username plus password |
| SSH key auth | Private key on your laptop, public key on the server |

### SSH Key Pair

```text
Public key  -> server
Private key  -> your laptop
```

### Useful Commands

```bash
ssh-keygen -t ed25519 -C "you@example.com"
ssh-copy-id user@server-ip
scp file.txt user@server-ip:/home/ubuntu
ssh user@server-ip "df -h"
```

### DevOps Use Cases

- Log into cloud servers
- Restart services remotely
- Copy deployment files
- Run admin commands safely

---

## 5. FTP / SFTP

### What Is FTP?

FTP transfers files between systems, but it is not encrypted.

### What Is SFTP?

SFTP is secure file transfer over SSH.

### FTP vs SFTP

| Feature | FTP | SFTP |
|---|---|---|
| Secure | No | Yes |
| Encryption | No | SSH |
| Port | 21 | 22 |
| Recommended | No | Yes |

### Useful Commands

```bash
sftp user@server-ip
put file.txt
get file.txt
```

### DevOps Use Cases

- Uploading deployment files
- Transferring backups
- Moving logs between systems

---

## 6. DNS

### What Is DNS?

DNS converts human-readable domain names into IP addresses.

Example:

```text
google.com -> IP address
```

### Why DNS Matters

Humans remember names. Servers route by IP.
DNS connects both.

### DNS Flow

```text
Browser
-> DNS resolver
-> Root DNS
-> TLD server
-> Authoritative DNS
-> IP address
-> Connection starts
```

### Common DNS Records

| Record | Purpose |
|---|---|
| A | Domain to IPv4 |
| AAAA | Domain to IPv6 |
| CNAME | Alias to another name |
| MX | Mail server |
| TXT | Verification and email records |
| NS | Name servers |

### Useful Commands

```bash
nslookup example.com
dig example.com
dig example.com MX
dig example.com TXT
dig -x 8.8.8.8
```

### DevOps Use Cases

- Point domain names to servers
- Configure email routing
- Verify SSL and email records
- Debug CDN or Kubernetes ingress setups

---

## 7. SMTP

### What Is SMTP?

SMTP is used to send email.

### SMTP Ports

| Port | Meaning |
|---|---|
| 25 | Server-to-server mail |
| 587 | Mail submission with STARTTLS |
| 465 | SMTP over SSL |

### Email Flow

```text
Sender -> SMTP server -> MX lookup -> Recipient SMTP server -> Mailbox
```

### Useful Commands

```bash
telnet mail.example.com 587
openssl s_client -connect mail.example.com:587 -starttls smtp
mailq
```

### DevOps Use Cases

- Password reset emails
- System alerts
- Transactional email services
- Build notifications from CI/CD

---

## 8. IMAP

### What Is IMAP?

IMAP lets email clients read mail while keeping it synced on the server.

### IMAP Ports

| Port | Meaning |
|---|---|
| 143 | IMAP, unencrypted |
| 993 | IMAPS, encrypted |

### IMAP vs POP3

| Protocol | Behavior |
|---|---|
| IMAP | Keeps mail on the server and syncs devices |
| POP3 | Downloads mail locally, often removes it from server |

### DevOps Use Cases

- Mail server setup with Dovecot
- Multi-device inbox sync
- Monitoring mailboxes in scripts

---

## 9. POP3S

### What Is POP3S?

POP3S is POP3 over SSL/TLS.

### Ports

| Port | Meaning |
|---|---|
| 110 | POP3, unencrypted |
| 995 | POP3S, encrypted |

### When To Use It

Use IMAP for modern setups. POP3 is mostly legacy.

---

## 10. SPF

### What Is SPF?

SPF is a DNS TXT record that lists which servers may send email for your domain.

### Example

```dns
v=spf1 ip4:192.0.2.1 include:sendgrid.net -all
```

### Meaning

| Part | Meaning |
|---|---|
| v=spf1 | SPF version |
| ip4:... | Allow this IP to send mail |
| include:... | Allow a third-party sender |
| -all | Reject all others |
| ~all | Soft fail |

### DNS Record Example

```text
Type: TXT
Name: @
Value: v=spf1 include:_spf.google.com ~all
```

---

## 11. DKIM

### What Is DKIM?

DKIM signs outgoing email so receivers can verify it was not altered.

### How It Works

```text
Mail server signs with private key
-> Receiver checks public key in DNS
-> Signature matches
-> Email is trusted
```

### DNS Record Example

```text
selector1._domainkey.example.com
TXT
v=DKIM1; k=rsa; p=PUBLIC_KEY_HERE
```

### Useful Commands

```bash
sudo opendkim-genkey -t -s selector1 -d example.com
dig selector1._domainkey.example.com TXT
```

---

## 12. DMARC

### What Is DMARC?

DMARC tells receiving servers what to do when SPF or DKIM fail.
It also enables reporting.

### DMARC Policy

| Policy | Meaning |
|---|---|
| none | Monitor only |
| quarantine | Send to spam |
| reject | Block the message |

### DNS Record Example

```text
_dmarc.example.com
TXT
v=DMARC1; p=quarantine; rua=mailto:dmarc-reports@example.com; pct=100
```

### Recommended Setup Order

1. Add SPF
2. Add DKIM
3. Add DMARC

---

## 13. Quick Comparison

### Email Protocol Summary

| Protocol | Purpose | Secure Port | Direction |
|---|---|---|---|
| SMTP | Send email | 587 or 465 | Outbound |
| IMAP | Read email on server | 993 | Inbound |
| POP3S | Download email | 995 | Inbound |

### Security Record Summary

| Record | Stored In | Purpose |
|---|---|---|
| SPF | DNS TXT | Allowed senders |
| DKIM | DNS TXT | Email signature |
| DMARC | DNS TXT | Policy and reports |

### Network Protocol Summary

| Protocol | Port | Encrypted | Use |
|---|---|---|---|
| HTTP | 80 | No | Web traffic |
| HTTPS | 443 | Yes | Secure web traffic |
| SSH | 22 | Yes | Remote access |
| SFTP | 22 | Yes | Secure file transfer |
| FTP | 21 | No | Legacy file transfer |
| DNS | 53 | No | Name resolution |
| SMTP | 25/587 | STARTTLS | Email sending |
| IMAP | 993 | Yes | Email reading |
| POP3S | 995 | Yes | Email download |

---

## 14. Starter Labs

### Lab 1: Create an SSH Key

```bash
ssh-keygen -t ed25519 -C "you@example.com"
ssh-copy-id user@server-ip
```

### Lab 2: Check DNS Records

```bash
dig example.com +short
dig example.com MX
dig example.com TXT
```

### Lab 3: Test HTTPS

```bash
curl -I https://example.com
openssl s_client -connect example.com:443
```

### Lab 4: Send a Test Email

```bash
echo "Test body" | mail -s "Test Subject" recipient@example.com
```

---

## 15. One-Line Revision

| Concept | Meaning |
|---|---|
| OSI | How data moves across a network |
| HTTP | Web communication |
| HTTPS | Secure web communication |
| TLS | Encryption layer |
| SSH | Secure remote access |
| FTP | File transfer |
| SFTP | Secure file transfer |
| DNS | Domain to IP lookup |
| SMTP | Send email |
| IMAP | Read email from server |
| POP3S | Download email securely |
| SPF | Allowed senders in DNS |
| DKIM | Email signature |
| DMARC | Policy for failed email checks |

---

## Best Beginner Takeaway

If you are new, focus on this chain first:

```text
DNS -> HTTP/HTTPS -> TLS -> SSH
```

Then add email:

```text
SMTP -> IMAP -> SPF -> DKIM -> DMARC
```

That order gives you the fastest path to real DevOps understanding.
