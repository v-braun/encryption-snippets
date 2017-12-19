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


## Self Signed SSL Certificate with key

**Kind:** certificate with encrypted key

**File Extensions:** .key and .crt

**Tool:**: openssl

**Plattform:** UNIX / WINDOWS

**Lifetime:** MAX 

**hint:** 

**1.:** 
On UNIX systems remove the first slash at -subj

**2.:** 
need SAN extension to work with Chrome 

*UNIX:* add:

    -config <(cat /System/Library/OpenSSL/openssl.cnf \
        <(printf '[SAN]\nsubjectAltName=DNS:localhost')) \

*Windows:*
add to 

    'C:\Program Files\Git\usr\ssl'
temporary

    [SAN]
    subjectAltName=DNS:localhost
  


**Command:**

```bash
openssl req \
    -newkey rsa:2048 \
    -x509 \
    -nodes \
    -keyout localhost.key \
    -new \
    -out localhost.crt \
    -subj "//CN=localhost" \
    -reqexts SAN \
    -extensions SAN \
    -sha256 \
    -days 3650
```    
