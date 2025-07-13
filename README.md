<h2 align="center"><b>Evilginx Campaign Toolset</b></h2>
<div align="center">
  <img width="350" height="350" alt="image" src="https://github.com/user-attachments/assets/af5c1977-ac31-49fa-a947-bd40a41ea6aa" />
</div>
<p align="center">
A toolset for creating evilginx proxy hosts and subfilters, with an advanced scanner that detects domains and common security patterns in JavaScript responses from secure sites.
</p>

--------------------------------------------
PROXY HOSTS CRAFTER TOOL
--------------------------------------------

https://proxy-hosts-generator.ct.ws

This tool crafts you proxy hosts in this format:

  - {phish_sub: 'example', orig_sub: 'example', domain: 'domain.com', session: false, is_landing: false, auto_filter: false}

Usage:

Insert one domain per line; this tool creates a proxy host for each line!

TLDs this tool will create proxy hosts for:

'com', 'net', 'org', 'io', 'cn','info', 'co', 'us', 'gov', 'edu','ru', 'uk', 'eu', 'xyz', 'me', 'tr', 'nl', 'it', 'se', 'gr', 'lv', 'kr', 'lt', 'fr', 'pl', 'ro', 'dev','asp', 'biz', 'pro', 'tech', 'ai', 'shop', 'online', 'site', 'live', 'social', 'ca', 'mx', 'de', 'es', 'bank', 'finance', 'money', 'invest', 'capital', 'credit', 'insurance'

Considerations:

For domains with no subdomain this tool will insert 'www' in phish_sub and orig_sub values

--------------------------------------------
SUBFILTERS CRAFTER TOOL
--------------------------------------------

https://sub-filter-generator.ct.ws

Usage:

Insert one domain per line; this tool creates a subfilter for each line!

TLDs this tool will create subfilters/replacements for:

'com', 'net', 'org', 'io', 'cn','info', 'co', 'us', 'gov', 'edu','ru', 'uk', 'eu', 'xyz', 'me', 'tr', 'nl', 'it', 'se', 'gr', 'lv', 'kr', 'lt', 'fr', 'pl', 'ro', 'dev','asp', 'biz', 'pro', 'tech', 'ai', 'shop', 'online', 'site', 'live', 'social', 'ca', 'mx', 'de', 'es', 'bank', 'finance', 'money', 'invest', 'capital', 'credit', 'insurance'

Considerations:

This tool might not handle ccTLDs correctly.

You should craft these subfilters with the same domains you created proxy hosts!

Subfilters genrated in this tool aim to rewrite URLs/Domains from a webpage's text/javascript, application/javascript, application/x-javascript, text/html, application/json, image/svg+xml, text/plain and font/woff2 to your phishing domain.

Example:

You insert example.domain.com in line one, this tool creates "triggers_on", "orig_sub" and "domain" based on example.domain.com (For domains with no subdomain this tool will insert 'www' in phish_sub and orig_sub values)

Let's assume "secure.institution.com" is present in "example.domain.com" for all the mime types:

- https://secure.institution.com will become https://secure.example.com
- https://secure\.institution\.com will become https://secure\.example\.com
- https://secure\\.institution\\.com will become https://secure\\.example\\.com
- http://secure.institution.com will become http://secure.example.com
- http://secure\.institution\.com will become http://secure\.example\.com
- http://secure\\.institution\\.com will become http://secure\\.example\\.com
- https%3A%2F%2Fsecure.institution.com will become https%3A%2F%2Fsecure.example.com
- https%3A%2F%2Fsecure\\.institution\.com will become https%3A%2F%2Fsecure\\.example\\.com
- https%3A%2F%2Fsecure\\\\.institution\\\\.com will become https%3A%2F%2Fsecure\\\\.example\\\\.com
- http%3A%2F%2Fsecure.institution.com will become http%3A%2F%2Fsecure.example.com
- http%3A%2F%2Fsecure\\.institution\.com will become http%3A%2F%2Fsecure\\.example\\.com
- http%3A%2F%2Fsecure\\\\.institution\\\\.com will become http%3A%2F%2Fsecure\\\\.example\\\\.com
- institution.com will become example.com
- institution\.com will become example\.com
- institution\\.com will become example\\.com

Let's assume "institution.com" (with no subdomain) is present in "example.domain.com" for all the mime types:

- https://institution.com will become https://example.com
- https://institution\.com will become https://example\.com
- https://institution\\.com will become https://example\\.com
- http://institution.com will become http://example.com
- http://institution\.com will become http://example\.com
- http://institution\\.com will become http://example\\.com
- https%3A%2F%2Finstitution.com will become https%3A%2F%2Fexample.com
- https%3A%2F%2Finstitution\\.com will become https%3A%2F%2Fexample\\.com
- https%3A%2F%2Finstitution\\\\.com will become https%3A%2F%2Fexample\\\\.com
- http%3A%2F%2Finstitution.com will become http%3A%2F%2Fexample.com
- http%3A%2F%2Finstitution\\.com will become http%3A%2F%2Fexample\\.com
- http%3A%2F%2Finstitution\\\\.com will become http%3A%2F%2Fexample\\\\.com
- institution.com will become example.com
- institution\.com will become example\.com
- institution\\.com will become example\\.com

Let's assume "secure.for.everyone.institution.com" (with various subdomains) is present in "example.domain.com" for all the mime types:

https://secure.for.everyone.institution.com will become https://secure.for.everyone.example.com
https://secure\.for\.everyone\.institution\.com will become https://secure\.for\.everyone\.example\.com
https://secure\\.for\\.everyone\\.institution\\.com will become https://secure\\.for\\.everyone\\.example\\.com
http://secure.for.everyone.institution.com will become http://secure.for.everyone.example.com
http://secure\.for\.everyone\.institution\.com will become http://secure\.for\.everyone\.example\.com
http://secure\\.for\\.everyone\\.institution\\.com will become http://secure\\.for\\.everyone\\.example\\.com
https%3A%2F%2Fsecure.for.everyone.institution.com will become https%3A%2F%2Fsecure.for.everyone.example.com
https%3A%2F%2Fsecure\\.for\\.everyone\\.institution\\.com will become https%3A%2F%2Fsecure\\.for\\.everyone\\.example\\.com
https%3A%2F%2Fsecure\\\\.for\\\\.everyone\\\\.institution\\\\.com will become https%3A%2F%2Fsecure\\\\.for\\\\.everyone\\\\.example\\\\.com
http%3A%2F%2Fsecure.for.everyone.institution.com will become http%3A%2F%2Fsecure.for.everyone.example.com
http%3A%2F%2Fsecure\\.for\\.everyone\\.institution\\.com will become http%3A%2F%2Fsecure\\.for\\.everyone\\.example\\.com
http%3A%2F%2Fsecure\\\\.for\\\\.everyone\\\\.institution\\\\.com will become http%3A%2F%2Fsecure\\\\.for\\\\.everyone\\\\.example\\\\.com
institution.com will become example.com
institution\.com will become example\.com
institution\\.com will become example\\.com

IMPORTANT!
Regexp might not handle ccTLDs correctly.

--------------------------------------------
CODE SCANNER
--------------------------------------------

https://code-scanner.ct.ws

Usage:

Paste a code in the input field and watch what security patterns and domains your code contains

Allowed TLDs for domain matching:

'com', 'net', 'org', 'io', 'cn','info', 'co', 'us', 'gov', 'edu','ru', 'uk', 'eu', 'xyz', 'me', 'tr', 'nl', 'it', 'se', 'gr', 'lv', 'kr', 'lt', 'fr', 'pl', 'ro', 'dev','asp', 'biz', 'pro', 'tech', 'ai', 'shop', 'online', 'site', 'live', 'social', 'ca', 'mx', 'de', 'es', 'bank', 'finance', 'money', 'invest', 'capital', 'credit', 'insurance'

Considerations:

This tool will output the entire line of the found keyword

This tool scans for the following keywords, which normally aim to anti-phishing protection when present in a code:

"integrity=", "<meta", "window.location", "csrfToken", "nonce=", "grecaptcha", "honeypot", "location.href", "document.domain", "location.hostname", "window.top", "window.self", "wasm", "window.trustedTypes", "MutationObserver", "crypto.subtle", "request.url", "request.domain", "navigator.userAgent", "navigator.webdriver", "navigator.languages", "navigator.connection", "eval(", "document.createElement", "window.alert", "responseurl", "navigator.permissions", "window.navigator.platform", "window.name", "window.frameElement", "window.parent", "window.opener", "document.hasFocus", "document.visibilityState", "document.referrer", "performance.navigation", "performance.now", "performance.getEntriesByType", "Content-Security-Policy", "X-Frame-Options", "sandbox", "SecurityPolicyViolationEvent", "performance.getEntriesByType", "crossOriginIsolated", "self.origin", "window.origin", "document.cookie", "localStorage", "sessionStorage", "indexedDB", "caches", "document.location.origin", "location.ancestorOrigins", "referrerPolicy", "top.location.href", "form.action", "addEventListener", "window.location.assign", "window.location.replace", "top !== self", "crossorigin=", "window.trustedTypes", "require-trusted-types-for", "frame-ancestors", "Permissions-Policy", "Feature-Policy", "Cross-Origin-Opener-Policy", "Cross-Origin-Resource-Policy", "fetch(", "Strict-Transport-Security"
