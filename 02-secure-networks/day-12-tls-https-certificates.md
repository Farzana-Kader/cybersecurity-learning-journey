Day 12 — TLS, HTTPS and Digital Certificates

1. Why do we need HTTPS?

Imagine logging into your bank account over a network.

If information is sent without encryption, an attacker who can observe the traffic may be able to read sensitive data. HTTPS protects HTTP communication using TLS (Transport Layer Security).

TLS provides three important security properties:
- Confidentiality: Encrypts data so unauthorized observers cannot normally read its contents.
- Integrity: Helps detect unauthorized modification of protected data.
- Authentication: Uses certificates to help verify the server's identity.

Your browser

Connects to a website using HTTPS.



TLS-protected communication

Data is encrypted in transit between the endpoints, subject to correct configuration and trusted endpoints.



Web server

Processes the request and sends a protected response.



Remember: HTTPS protects data in transit, but it does not guarantee that a website is honest, free from malware, or safe to use. Phishing websites can also use HTTPS.

2. How does a TLS handshake work?

Before exchanging protected application data, the browser and server negotiate security settings and establish shared cryptographic keys.

1. Client Hello

The browser proposes TLS versions and cryptographic options.

2. Server response

The server selects parameters and provides its certificate.

3. Certificate validation

The browser checks the certificate's trust chain, hostname and validity.

4. Key establishment

The endpoints establish shared session keys using the negotiated method.

5. Protected communication

Application data is sent using authenticated encryption.


This is a simplified overview. TLS 1.3 usually completes its handshake in fewer round trips than older TLS versions, and the exact messages depend on the negotiated protocol.

3. What is a digital certificate?

A digital certificate binds a public key to an identity, such as a website's domain name. It is typically issued and digitally signed by a Certificate Authority (CA).


Website certificate

Contains information such as the domain names covered, public key, issuer, validity period and digital signature.




Certificate Authority (CA)

Signs certificates to help browsers establish a chain of trust to a trusted root certificate.



When a browser validates a certificate, it checks several things, including:
- Whether the certificate is valid for the requested hostname.
- Whether its validity dates are appropriate.
- Whether its signature chain leads to a trusted CA.
- Whether other applicable checks, such as revocation or certificate constraints, are satisfied.

Cybersecurity example: If an attacker presents an untrusted or hostname-mismatched certificate, the browser may display a security warning. Never ignore certificate warnings on banking, email, or other sensitive websites without understanding the cause.

4. Symmetric vs asymmetric encryption

TLS uses cryptography in different ways.

Feature	Symmetric encryption	Asymmetric cryptography

Keys	Same secret key encrypts and decrypts	Uses a public/private key pair

Typical role in TLS	Protects application data efficiently	Supports authentication and key establishment, depending on the handshake

Performance	Generally fast	Generally more computationally expensive

Examples	AES-GCM, ChaCha20-Poly1305	RSA, elliptic-curve cryptography

A key distinction: modern TLS does not normally encrypt every webpage directly with the website's public key. Instead, the handshake establishes shared secret material from which symmetric session keys are derived.

Also, a public key can be shared openly; its corresponding private key must remain protected.

5. What can a network investigator see when traffic uses HTTPS?

HTTPS protects the contents of application data in transit, but it doesn't make all network activity invisible.

Depending on the protocol and network setup, an investigator may still be able to observe:
- Source and destination IP addresses.
- Connection times, duration and data volumes.
- The destination port.
- Some DNS information, if it is not separately encrypted.
- Some TLS handshake metadata, depending on the TLS version and features used.

For example, an analyst may identify a suspicious connection from a device to an unfamiliar server even if the webpage contents remain encrypted.

This is why network defenders combine traffic metadata, endpoint logs, DNS records and other evidence instead of relying on packet contents alone.

Practical task — Inspect HTTPS on Windows

You can explore TLS without scanning any external system.

Task A — Inspect a website's certificate
1. Open a trusted website in your browser.
2. Click the site-information or connection icon beside its address.
3. Open the connection-security or certificate information, if available.
4. Find the certificate issuer, validity dates and domain names.

Browser menus differ, and the connection icon does not always look like a padlock.


Task B — Check HTTPS connectivity

Open PowerShell and run:

Test-NetConnection example.com -Port 443

This checks TCP connectivity to port 443. It does not, by itself, verify that the TLS certificate is valid.


Day 12 quiz

1. What does HTTPS use to protect HTTP communication?

ARP

TLS

DHCP

FTP

Correct! TLS


2. What is a primary purpose of a website's digital certificate?

Guarantee the website has no malware

Bind a public key to an identity such as a domain name

Hide the server's IP address

Replace all passwords

Correct! Bind a public key to an identity such as a domain name



3. Which type of cryptography normally protects TLS application data efficiently?

Symmetric encryption

Hashing alone

DNS resolution

ARP

Correct! Symmetric encryption



4. What should a browser check when validating a website certificate?

Only the website's page colour

Only the server's port number

Hostname, validity and certificate trust chain

The user's desktop wallpaper

Correct! Hostname, validity and certificate trust chain


5. What can an investigator often still observe about HTTPS traffic?

All encrypted message contents in plaintext

Connection metadata such as IP addresses, timing and traffic volume

Every user's password automatically

Nothing at all

Correct! Connection metadata such as IP addresses, timing and traffic volume

Score: 5/5
