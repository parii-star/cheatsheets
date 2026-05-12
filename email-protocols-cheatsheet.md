# Email Protocols Cheat Sheet

> **Goal:** Understand the main email protocols clearly enough to know what each one does and which port to check.

This sheet explains the basic mail flow in plain language first, then lists the ports.

## Big Picture

Email usually moves in two steps:

1. You send a message from your email app to your mail server.
2. The mail server delivers it to the recipient's mail server.

When you read mail, your app talks to your mail server again to fetch or sync messages.

## Quick Memory Trick

| Protocol | Think of it as |
|---|---|
| SMTP | sending mail |
| IMAP | reading mail while leaving it on the server |
| POP3 | downloading mail to your device |

## Essential Ports Reference

| Port | Explanation |
|---|---|
| `25` | SMTP delivery |
| `587` | SMTP submission |
| `993` | Secure IMAP |

## SMTP

SMTP means Simple Mail Transfer Protocol.

Use SMTP when a message is being sent.

| Item | Plain Meaning |
|---|---|
| `SMTP` | the protocol used to send email |
| `25` | server-to-server mail delivery |
| `587` | mail submission from an email app |
| `465` | encrypted mail submission, older but still common |

Think of `587` as the normal port for sending mail from your email app. Think of `25` as the port mail servers use to pass messages to each other.

Example:

```bash
telnet [host] 25
```

## IMAP

IMAP means Internet Message Access Protocol.

Use IMAP when you want all your devices to show the same mailbox.

| Item | Plain Meaning |
|---|---|
| `IMAP` | keeps mail on the server and syncs it to your devices |
| `143` | standard IMAP port |
| `993` | IMAP with TLS encryption |

With IMAP, deleting, reading, or moving a message usually changes the mailbox on the server too.

## POP3

POP3 means Post Office Protocol version 3.

Use POP3 when a client downloads mail and often keeps a local copy.

| Item | Plain Meaning |
|---|---|
| `POP3` | downloads mail from the server to one device |
| `110` | standard POP3 port |
| `995` | POP3 with TLS encryption |

POP3 is simpler than IMAP, but it is less convenient if you use more than one device.

## Common Ports

| Protocol | Port | What It Is For |
|---|---|---|
| SMTP | `25` | server-to-server delivery |
| SMTP submission | `587` | sending mail from a client app |
| SMTPS | `465` | encrypted mail submission |
| IMAP | `143` | reading mailbox content |
| IMAPS | `993` | encrypted mailbox access |
| POP3 | `110` | downloading mail |
| POP3S | `995` | encrypted mail download |

If you only want to remember the important ones, start with `587` for sending, `993` for reading with IMAP, and `995` for POP3.

## How Mail Flows

Example flow:

1. Your email app connects to your mail server on `587`.
2. Your mail server sends the message to the recipient's server on `25`.
3. The recipient reads the message with `IMAP` on `993` or `POP3` on `995`.

## Diagnostics

| Command | What It Helps You Check |
|---|---|
| `nslookup -type=mx [domain]` | which mail servers handle a domain |
| `dig mx [domain]` | the domain's MX records in more detail |
| `openssl s_client -connect [host]:[port]` | whether TLS works and what the server says |
| `telnet [host] [port]` | whether a TCP port is reachable |

Example:

```bash
dig mx example.com
openssl s_client -connect mail.example.com:993
```

## Fast Summary

| If You Want To... | Use |
|---|---|
| send mail | SMTP |
| read the same mailbox on multiple devices | IMAP |
| download mail to one device | POP3 |

## Where DevOps Engineers Use This

You mainly need to know:

- which service uses which port
- what traffic should be allowed in firewall or security groups
- how to troubleshoot email alerts and mail delivery

These are the most important email-related ports for DevOps.

| Port | Protocol | Why It Matters |
|---|---|---|
| `25` | SMTP | Server-to-server mail delivery |
| `587` | SMTP Submission | Apps and tools send mail |
| `465` | SMTPS | Encrypted SMTP |

Use SMTP when you are setting up application alerts, password resets, monitoring notifications, or any outbound mail from a server. Use the port table above when you are checking firewall rules, cloud security groups, or mail server access.


