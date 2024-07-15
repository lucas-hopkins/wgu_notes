
Hypertext history

Tim Berners-Lee's ideas of creating linking webpages was founded on previous work on hypertext:

- 1945: Engineer Vannevar Bush writes the essay "As We May Think" that describes Memex, a theoretical machine for building and following links between documents.
- 1965: Ted Nelson coins the term _HyperText_ in a paper on how to deal with information that was complex, changing, and uncertain.
- 1968: Doug Engelbart demonstrates an implementation of hyperlinks with a mouse in the oN-Line System (NLS).
- 1987: Apple releases HyperCard, software for the Macintosh that enables programming hypertext applications.

- Typical IP Address has 32 bits divided into four 8-bit groups.

- The original Internet Protocol, known as IPv4, has 32-bit addresses. 32 bits can represent 232 or about 4 billion unique addresses, originally believed to be more than enough, but 4 billion is no longer enough. 
- A new version of the Internet Protocol, IPv6, uses 128-bit addresses, capable of representing 2128 addresses. The number 2128 is 3.4 × 1038 or 340,000,000,000,000,000,000,000,000,000,000,000,000, which is hopefully enough for quite a while. IPv4 and IPv6 currently co-exist and likely will for a long time.

## Domain Names
### Registering a domain name
Anyone may register an unused domain name with a domain name registrar. Most registrars charge a yearly fee for keeping the domain registered. Registration information is made publicly available from ICANN's [Whois](https://whois.icann.org/) service.

Domain names are hierarchical. A domain name belongs to one of numerous top-level domains (TLD), such as .com, .net, .org, .edu, and .gov. Also, each country is assigned a unique two-letter country code top-level domain (ccTLD) like .uk (United Kingdom), .ru (Russia), and .de (Germany). IANA, the organization that manages TLDs, allows companies and organizations to create customized TLDs, like .church, .pizza, and .music.

https://data.iana.org/TLD/tlds-alpha-by-domain.txt
## URLs

A URL is composed of several parts:

- Scheme - Characters at the beginning of a URL followed by a colon ":" or a colon and double slashes "://". Common URL schemes include `http`, `https`, `mailto`, and `file`. Ex: In https://www.cdc.gov/alcohol, the scheme is "https".
    
- Hostname - The complete domain name following the scheme in a URL. Ex: In https://www.cdc.gov/alcohol, the hostname is "www.cdc.gov".
    
- Path - The characters to the right of the hostname in a URL. Ex: In https://www.cdc.gov/alcohol, the path is "/alcohol".
    
- Query string - Optional characters to the right of the question mark (?) in a URL that provide data for the web server. In https://www.youtube.com/watch?v=uu7XCEMdSHg, the characters after the ? tells YouTube's server to play a video having code uu7XCEMdSHg.
    
- Fragment - Optional characters at the end of a URL that start with a hash character (#) and refer to a certain location within a webpage. In https://en.wikipedia.org/wiki/URL#History, the fragment "#History" refers to the webpage's History section.

https://url.spec.whatwg.org/


## HTTP

The HyperText Transfer Protocol (HTTP) is a networking protocol that runs over TCP/IP and governs communication between web browsers and web servers. Transmission Control Protocol/Internet Protocol (TCP/IP) is a protocol suite that governs how data packets are transferred over the internet from one machine to another. Understanding the details of TCP/IP is not usually required of web developers, but a thorough understanding of HTTP is necessary to create effective web applications.

HTTP/1.1 is the HTTP standard used for most of the web's lifetime, but many websites are adopting HTTP/2, a relatively new HTTP standard that speeds-up the transfer of information between web browsers and web servers. HTTP/2 maintains most of HTTP/1.1's semantics. HTTP/3, currently in development, improves the speed of HTTP/2 by using UDP to transport data packets instead of TCP. This material focuses on the basic HTTP workings that all standards share.

Web browsers often use ETags to aid in caching web resources. An entity tag (ETag) is an identifier for a specific version of a web resource. Ex: 34905a3e285dd11. When the resource changes, so should the ETag associated with the resource. When a web browser requests a cached web resource, the browser sends the ETag in the request with an `If-None-Match` header. The web server will reply with a 304 Not Modified response status if the resource has not changed or a 200 OK with the changed resource and a new ETag.

HTTP defines additional HTTP headers to aid in caching:

- If-Modified-Since is used with the `Last-Modified` date/time to request the web server only send the requested resource if the resource has changed since the specified date/time. Ex: "If-Modified-Since: Wed, 01 Sep 2019 13:24:52 GMT" asks the web server to send the resource if the resource was modified after Sep 1, 2019 at 13:24:52 GMT.
    
- Expires contains a date/time indicating when the requested resource is considered "stale". Ex: "Expires: Wed, 01 Sep 2019 13:24:52 GMT" tells the web browser to show the cached resource until Sep 1, 2019 at 13:24:52 GMT.
    
- Cache-Control is used to specify a number of caching directives. Ex: "Cache-Control: no-store" tells the web browser to never cache the requested resource, and "Cache-Control: max-age=180" tells the browser to cache the resource for 180 seconds.

Web developers can view 304 Not Modified responses in Chrome's DevTools by opening the Network tab and ensuring the checkbox labeled "Disable cache" is not checked.

