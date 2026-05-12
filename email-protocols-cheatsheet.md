# Email Protocols & Security Cheat Sheet

> Beginner-Friendly + DevOps Engineer Focused

---

## Table of Contents

1. [SMTP](#smtp)
2. [SPF](#spf)
3. [DKIM](#dkim-domain-keys)
4. [DMARC](#dmarc)

---

## Big Picture: How Email Works

When you send an email:

```text
Your Mail App
↓
SMTP Server
↓
Internet
↓
Recipient Mail Server
↓
Recipient Inbox
```

Example:

```text
You send mail from Gmail → Outlook receives it
```

But before accepting the email, the receiver checks:

* Is sender genuine?
* Is email fake/spam?
* Was email modified?

That is where:

* SPF
* DKIM
* DMARC

become important.

---

## Complete Email Security Flow

```text
1. User sends email
2. SMTP transfers email
3. Receiver checks SPF
4. Receiver checks DKIM signature
5. Receiver applies DMARC policy
6. Email delivered or rejected
```

---

## 1. SMTP

### What is SMTP?

SMTP = Simple Mail Transfer Protocol

Used to:

```text
SEND emails
```

SMTP does NOT fetch emails.

It only transfers mail between:

* Mail client → Mail server
* Mail server → Mail server

---

### Real Example

```text
You send email from Gmail
↓
Gmail SMTP server processes it
↓
Email delivered to Outlook server
```

---

### SMTP Flow

```text
Mail App
↓
SMTP Server
↓
Recipient SMTP Server
↓
Recipient Mailbox
```

---

### SMTP Ports

| Port | Purpose                        |
| ---- | ------------------------------ |
| 25   | Server-to-server mail transfer |
| 587  | Secure mail submission         |
| 465  | SMTPS (SMTP over SSL/TLS)      |

---

### Why Port 25 Important?

Used mainly between mail servers.

Example:

```text
Gmail server → Yahoo server
```

Many cloud providers block port 25 to prevent spam.

---

### SMTP Authentication

Before sending email:

```text
Username + Password required
```

OR OAuth authentication.

---

### DevOps Engineer Usage

| Task                      | Why Important        |
| ------------------------- | -------------------- |
| Configure SMTP server     | Send app emails      |
| Debug email delivery      | Production support   |
| Configure alerts          | Monitoring systems   |
| Application notifications | Password reset mails |
| CI/CD alerts              | Build notifications  |

---

### Useful SMTP Commands

#### Test SMTP Connection

```bash
telnet smtp.gmail.com 587
```

#### OpenSSL SMTP Test

```bash
openssl s_client -connect smtp.gmail.com:465
```

---

### Common SMTP Errors

| Error | Meaning               |
| ----- | --------------------- |
| 550   | Mail rejected         |
| 535   | Authentication failed |
| 421   | Service unavailable   |
| 554   | Spam detected         |

---

## 2. SPF

### What is SPF?

SPF = Sender Policy Framework

SPF tells:

```text
"Which mail servers are allowed to send emails for my domain"
```

---

### Why SPF Needed?

Without SPF:

```text
Anyone can pretend to send email from your domain
```

Example fake mail:

```text
support@amazon.com
```

could be sent by attackers.

---

### SPF Prevents Spoofing

Receiver checks:

```text
"Is this server authorized?"
```

If YES → email accepted.

If NO → suspicious/spam.

---

### SPF Uses DNS TXT Record

Example SPF Record:

```dns
v=spf1 include:_spf.google.com ~all
```

---

### SPF Record Breakdown

| Part    | Meaning              |
| ------- | -------------------- |
| v=spf1  | SPF version          |
| include | Allowed provider     |
| ~all    | Soft fail for others |

---

### SPF Flow

```text
Email arrives
↓
Receiver checks domain DNS
↓
SPF TXT record found
↓
Sending server verified
↓
Pass or Fail
```

---

### Common SPF Qualifiers

| Symbol | Meaning   |
| ------ | --------- |
| +all   | Allow     |
| -all   | Hard fail |
| ~all   | Soft fail |
| ?all   | Neutral   |

---

### DevOps Engineer Responsibilities

| Task                             | Purpose          |
| -------------------------------- | ---------------- |
| Configure SPF                    | Prevent spoofing |
| Update DNS TXT records           | Mail validation  |
| Allow third-party mail providers | Gmail/SendGrid   |
| Debug SPF failures               | Email delivery   |

---

### Check SPF Record

#### Dig Command

```bash
dig TXT example.com
```

#### Nslookup

```bash
nslookup -type=TXT example.com
```

---

### SPF Limitation

SPF checks:

```text
Sending server only
```

It does NOT verify:

* email content
* message tampering

That is why DKIM exists.

---

## 3. DKIM (Domain Keys)

### What is DKIM?

DKIM = DomainKeys Identified Mail

DKIM adds:

```text
Digital Signature to email
```

to prove:

* Email is genuine
* Email content was NOT modified

---

### Easy Understanding

Think of DKIM like:

```text
A sealed signature on a document
```

If modified:

```text
Signature becomes invalid
```

---

### How DKIM Works

```text
1. Sending server signs email
2. Signature added in header
3. Public key stored in DNS
4. Receiver verifies signature
```

---

### DKIM Flow

```text
Email Sent
↓
Private Key signs email
↓
DKIM Signature attached
↓
Receiver fetches public key from DNS
↓
Signature verified
```

---

### DKIM Uses Two Keys

| Key         | Stored Where   |
| ----------- | -------------- |
| Private Key | Mail server    |
| Public Key  | DNS TXT record |

---

### Example DKIM Record

```dns
selector._domainkey.example.com
```

TXT record contains public key.

---

### What DKIM Protects

| Protected?          | Yes/No |
| ------------------- | ------ |
| Sender authenticity | Yes    |
| Message integrity   | Yes    |
| Encryption          | No     |

---

### DKIM vs SPF

| SPF                     | DKIM                     |
| ----------------------- | ------------------------ |
| Verifies sending server | Verifies email signature |
| DNS TXT record          | DNS TXT record           |
| Prevents spoofing       | Prevents tampering       |

---

### DevOps Engineer Usage

| Task                     | Purpose           |
| ------------------------ | ----------------- |
| Configure DKIM           | Mail authenticity |
| Rotate keys              | Security          |
| DNS setup                | Verification      |
| Debug signature failures | Deliverability    |

---

### Check DKIM

#### Dig DKIM Record

```bash
dig TXT selector._domainkey.example.com
```

---

## 4. DMARC

### What is DMARC?

DMARC = Domain-based Message Authentication, Reporting & Conformance

DMARC tells receiving servers:

```text
"What to do if SPF or DKIM fails"
```

---

### Why DMARC Important?

Without DMARC:

```text
Receiver may still accept suspicious email
```

DMARC gives clear policy.

---

### DMARC Depends On

DMARC works using:

* SPF
* DKIM

DMARC itself does NOT replace them.

---

### DMARC Flow

```text
Email Received
↓
SPF Check
↓
DKIM Check
↓
DMARC Policy Applied
↓
Accept / Reject / Spam
```

---

### DMARC Policies

| Policy     | Meaning      |
| ---------- | ------------ |
| none       | Monitor only |
| quarantine | Send to spam |
| reject     | Reject email |

---

### Example DMARC Record

```dns
v=DMARC1; p=reject; rua=mailto:admin@example.com
```

---

### DMARC Record Breakdown

| Part     | Meaning              |
| -------- | -------------------- |
| v=DMARC1 | Version              |
| p=reject | Reject failed emails |
| rua      | Reporting email      |

---

### DMARC Reports

Receivers send reports about:

* SPF failures
* DKIM failures
* Spoof attempts

Useful for monitoring attacks.

---

### DevOps Engineer Responsibilities

| Task                        | Purpose             |
| --------------------------- | ------------------- |
| Configure DMARC             | Prevent spoofing    |
| Analyze reports             | Security monitoring |
| Improve mail deliverability | Production systems  |
| Protect company domain      | Brand security      |

---

## Recommended Email Security Setup

```text
1. Configure SPF
2. Configure DKIM
3. Configure DMARC
4. Enforce reject policy
5. Monitor reports
```

---

## Email Authentication Comparison

| Technology | Main Purpose                |
| ---------- | --------------------------- |
| SMTP       | Send emails                 |
| SPF        | Verify sending server       |
| DKIM       | Verify email integrity      |
| DMARC      | Apply email security policy |

---

## Complete Email Security Architecture

```text
Your App
↓
SMTP Server
↓
Email Sent
↓
Receiver Server
├── SPF Check
├── DKIM Verification
└── DMARC Policy
↓
Inbox / Spam / Reject
```

---

## DNS Records Used in Email Security

| Record Type | Used For       |
| ----------- | -------------- |
| MX          | Mail server    |
| TXT         | SPF/DKIM/DMARC |
| A           | Mail server IP |

---

## Important Commands

| Command                | Purpose            |
| ---------------------- | ------------------ |
| dig TXT domain.com     | Check SPF          |
| dig MX domain.com      | Check mail servers |
| nslookup               | DNS lookup         |
| openssl s_client       | TLS debugging      |
| telnet smtp.server 587 | SMTP testing       |

---

## Most Important Concepts For DevOps Beginners

### Must Understand Clearly

* SMTP sends mail
* SPF verifies sender server
* DKIM verifies email integrity
* DMARC decides action
* DNS stores authentication records
* TLS secures email traffic

---

## One-Line Revision

| Concept | One-Line Meaning        |
| ------- | ----------------------- |
| SMTP    | Protocol to send emails |
| SPF     | Allowed mail servers    |
| DKIM    | Email digital signature |
| DMARC   | Email security policy   |

---

## Final Big Picture

```text
SMTP → Sends Email
SPF → Checks sender legitimacy
DKIM → Checks message integrity
DMARC → Decides trust policy
```
