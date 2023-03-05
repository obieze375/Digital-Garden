[[Index]] 

# How DNS work

The DNS protocol runs over UDP and uses port 53.

DNS is commonly employed by other application-layer protocols—including HTTP, SMTP, and FTP—to translate user-supplied hostnames to IP addresses. As an example, consider what happens when a browser (that is, an HTTP client), running on some user’s host, requests the URL www.someschool.edu/ index.html. In order for the user’s host to be able to send an HTTP request mes- sage to the Web server www.someschool.edu, the user’s host must first obtain the IP address of www.someschool.edu. This is done as follows.

1. The same user machine runs the client side of the DNS application.
2. The browser extracts the hostname, www.someschool.edu, from the URL
and passes the hostname to the client side of the DNS application.
3. The DNS client sends a query containing the hostname to a DNS server.
4. The DNS client eventually receives a reply, which includes the IP address for
the hostname.
5. Once the browser receives the IP address from DNS, it can initiate a TCP con-
nection to the HTTP server process located at port 80 at that IP address.

### DNS record types

DNS records, also known as zone files, provide information about a domain. This includes the IP address that is associated with this domain and how to handle queries for it. Each DNS record has a time-to-live setting (TTL) which indicates how often a DNS server will refresh it. 

Below are the most commonly used types of DNS records and their meaning.

<table><tbody><tr><td><strong>Type</strong></td><td><strong>Name</strong></td><td><strong>Description</strong></td></tr><tr><td>A</td><td>Host address</td><td>The most basic and the most commonly used DNS record. It translates human-friendly domain names into computer-friendly IP addresses.<br></td></tr><tr><td>AAAA</td><td>IPv6 host address</td><td>Same as A but for IPv6 (a host address that can have more than one IP address).</td></tr><tr><td>CNAME</td><td>Canonical name for an alias</td><td>Maps a name to another name. It should only be used when there are no other records on that name.<br></td></tr><tr><td>ALIAS</td><td>Auto resolved alias</td><td>Maps a name to another name, but can coexist with other records on that name.</td></tr><tr><td>MX</td><td>Mail eXchange</td><td>Specifies the e-mail server(s) responsible for a domain name.</td></tr><tr><td>NS</td><td>Name Server</td><td>Identifies the DNS servers responsible for a zone. One NS record for each DNS server in a zone.</td></tr><tr><td>TXT</td><td>Descriptive Text</td><td>Holds general information about a domain name such as who is hosting it, contact person, phone numbers, etc. Widely used for domain ownership verification.<br></td></tr></tbody></table>


