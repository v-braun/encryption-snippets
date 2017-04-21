# encryption-snippets

Some snippets to generate secrets, keys, certificates

## Self Signed SSL Certificate

**Kind:** plain certificate with plain key

**File Extensions:** .pem and .crt

**Tool:**: openssl

**Plattform:** UNIX

**Lifetime:** MAX 

**Command:**

```bash
openssl req -x509 -nodes -days 24800 -newkey rsa:2048 -keyout private-key-plain.pem -out certificate.crt
```
