
# DNS (Domain Name System)

**DNS (Domain Name System)** is used to convert human-readable domain names into machine-readable IP addresses. It provides a simple way for us to communicate with devices on the internet without having to remember complex numbers.

---
<br>

<img src="https://github.com/kalyank24/SOC-Progress/blob/main/DNS%20in%20Detail/images/Hierarchy.png" alt="Hierarchy">
## Domain Hierarchy

### Top-Level Domain (TLD)

A **Top-Level Domain (TLD)** is the rightmost part of a domain name.

There are two main types of TLDs:

* **gTLD (Generic Top-Level Domain)** – Examples include `.com`, `.org`, and `.net`.
* **ccTLD (Country Code Top-Level Domain)** – Examples include `.uk`, `.in`, and `.us`.

### Second-Level Domain

For example, in `tryhackme.com`:

* `.com` is the **TLD**.
* `tryhackme` is the **Second-Level Domain (SLD)**.

When registering a domain name, the second-level domain can contain up to **63 characters** and can include letters (`a-z`), numbers (`0-9`), and hyphens.

### Subdomain

A **subdomain** is located on the left-hand side of the second-level domain and is separated using a period (`.`).

For example:

```text
blog.tryhackme.com
```

Here, `blog` is the subdomain.

Subdomains follow similar restrictions as second-level domains. Multiple subdomains can also be used, separated by periods, to create longer domain names.

---

# DNS Record Types

DNS records contain information that tells DNS servers how a domain should be handled.

### 1. A Record

An **A record** stores or returns the **IPv4 address** associated with a domain name.

Example:

```text
example.com → 192.168.1.10
```

### 2. AAAA Record

An **AAAA record** stores or returns the **IPv6 address** associated with a domain name.

### 3. MX Record

**MX (Mail Exchange) records** specify the mail servers responsible for handling email for a domain.

MX records also contain a **priority value**, which tells the mail client which mail server to try first.

### 4. TXT Record

**TXT records** are text fields where domain owners can store various types of text-based information.

TXT records have multiple uses. One common use is specifying which servers are authorized to send emails on behalf of a domain.

---

# Making a DNS Request

<img src="https://github.com/kalyank24/SOC-Progress/blob/main/DNS%20in%20Detail/images/Request.png" alt="Request">

When you request a domain name, the DNS resolution process generally works as follows:

### 1. Local Cache

When a domain name is requested, your computer first checks its **local DNS cache** to see if it has recently looked up the domain.

If the information is not available in the local cache, the request is sent to a **Recursive DNS Server**.

### 2. Recursive DNS Server

The **Recursive DNS Server** is usually provided by your ISP, although users can also configure other public DNS servers.

The recursive DNS server maintains its own cache of frequently requested domain names. If the requested information is already cached, it can return the result without performing another lookup.

If the information is not available in its cache, it continues the DNS lookup process by querying other DNS servers.

### 3. Root DNS Server

The **Root DNS Servers** form the top level of the DNS hierarchy. Their job is to direct the recursive DNS server to the appropriate **TLD server** based on the requested domain.

For example, a request for `example.com` would be directed toward the `.com` TLD infrastructure.

### 4. Authoritative DNS Server

An **Authoritative DNS Server** is responsible for storing the DNS records for a particular domain.

It contains the authoritative information for the domain, such as its IP address, mail servers, and other DNS records.

The authoritative server provides the requested DNS record to the recursive DNS server, which can then cache the result for future requests.

---

## TTL (Time To Live)

DNS records contain a **TTL (Time To Live)** value.

The TTL specifies how long a DNS record can be cached before it needs to be queried again.

TTL values are measured in **seconds**.

For example, if a DNS record has a TTL of `3600`, it can be cached for **3600 seconds (1 hour)** before the resolver needs to obtain updated information.
