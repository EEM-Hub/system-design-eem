---
source: sources/wiki-Email.md
source_url: https://en.wikipedia.org/wiki/Email
---

## Email: Architecture, Protocols, and Message Format

Email (electronic mail) is a store-and-forward digital messaging system operating primarily over the Internet. Messages travel through a chain of agents — from the sender's mail user agent (MUA) through mail submission agents (MSA), mail transfer agents (MTA), and mail delivery agents (MDA) — before reaching the recipient's mailbox. The system prioritizes reliability over speed, with messages queued and retried for up to five days before permanent failure notification.

## Key Concepts

- **Store-and-forward model**: Neither sender nor recipient must be online simultaneously; servers accept, queue, forward, and store messages independently
- **Email address format**: `local-part@domain-name` — the local part typically identifies the user, the domain identifies the mail server
- **Envelope vs. Content**: An email has an *envelope* (routing information used by SMTP) and *content* (header + body). The envelope addresses can differ from header addresses (To/From fields)
- **Message structure**: Header section (structured fields like From, To, Subject, Date) separated from the body by a blank line
- **MIME (Multipurpose Internet Mail Extensions)**: Extended email beyond 7-bit ASCII to support multimedia content, non-Latin character sets, and attachments via quoted-printable and base64 encodings
- **Open mail relays**: MTAs that accept messages for any recipient — once common for reliability, now rare due to spam exploitation
- **Content formats**: Plain text, HTML, and Microsoft RTF; HTML adds links/images/formatting but increases size and attack surface (phishing, web bugs, malware vectors)

## Commands and Syntax

- **Email address syntax**: `user@domain.tld` (introduced 1971 on ARPANET with the @ symbol)
- **URI scheme**: `mailto:user@example.com` — opens the user's mail client with the address in the To: field; supports query parameters for Subject, CC, etc.
- **Required header fields** (per RFC 5322): `From:` and `Date:` are mandatory; `To:`, `Subject:`, `Cc:`, `Bcc:`, `Message-ID:`, `In-Reply-To:`, `References:` are common
- **Trace fields added by servers**: `Received:` (inserted at top of header by each SMTP server, last-to-first order) and `Return-Path:` (inserted by final delivery server)
- **Authentication trace fields**: `Authentication-Results`, `Received-SPF`, `DKIM-Signature`
- **File extensions**: `.eml` (MIME plain text, widely supported), `.emlx` (Apple Mail), `.msg` (Microsoft Outlook), `.mbx` (mbox-based)
- **Mailbox storage formats**: Maildir (one file per message) and mbox (single file)

## Relationships

- **SMTP** (Simple Mail Transfer Protocol): Core transport protocol for sending/relaying messages between servers; implemented on ARPANET in 1983
- **POP3** (Post Office Protocol): Retrieval protocol — typically downloads mail to client
- **IMAP** (Internet Message Access Protocol): Retrieval protocol — typically keeps mail on server with synchronized access
- **DNS/MX Records**: Domain Name System resolves recipient domain to mail exchange servers via MX records, enabling message routing
- **SPF, DKIM, DMARC**: Email authentication mechanisms that add trace/verification fields to prevent spoofing
- **Webmail**: Browser-based access (Gmail, Yahoo Mail) that bundles MUA/MTA/MDA functions — mail stays server-side
- **RFC lineage**: RFC 733 (ARPANET) → RFC 822 (1982) → RFC 2822 (2001) → RFC 5322 (2008, current standard)

## Exam-Relevant Points

- **Mandatory header fields**: Only `From:` and `Date:` are required by RFC 5322
- **The To: field can differ from actual delivery addresses** — SMTP envelope controls routing, not the header
- **Header field line limits**: Recommended 78 characters, hard limit 998 characters
- **MX record lookup**: The sending MTA queries DNS for the recipient domain's MX records to find the destination mail server
- **Agent roles**: MUA (user client) → MSA (submission) → MTA (transfer/relay) → MDA (final delivery)
- **Bounce obligation**: An MTA that accepts a message is obligated to deliver it or send a bounce message back to the sender
- **MIME encodings**: Quoted-printable (mostly 7-bit content with occasional non-ASCII) vs. base64 (arbitrary binary data)
- **Retry window**: Messages can be queued and retried for up to 5 days before permanent failure
- **Received header ordering**: Each server prepends (not appends) its Received: field, so trace reads last-hop-first
- **International email**: UTF-8 addresses standardized but not widely adopted; supported by Google and Microsoft
