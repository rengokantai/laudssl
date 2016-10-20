# laudssl
##1. What is SSL
###7 Understanding SSL transactions
####00:47
What's in a certificate?
- issuer of the certificate(CA)
- expiration data
- serial number


##2 How Do SSL Certificates work
###1 How do self-signed certificates work?
####01:04 
A ROOT CA is a top-level certificate authority. It has the authority to create certificates at the topmost hierarchical level of that organizational structure.
Its authenticity can't be revoked though, ever, by anybody.  

Because if it's ever destroyed, then every certificate that that certificate authority is responsible for, will become invalid, and will not be trusted by the chain up the chain to that ROOT certificate

###2 How do public trusted certificates work?
Private root certificates are signed by themselves because there is no higher authority in their chain to sign them. 
Root certificates from a certificate authority, on the other hand, are also signed by themselves because there's no higher authority in their chain. 
So they're really, really similar. The difference is that a trusted internet certificate authority will rarely, if ever, deliver you a certificate that's signed directly by the private key from their root certificate, but instead will give you a certificate signed by their intermediate certificate.


####08:53
private CA isa the same as public CA.  
The difference is that Apple, Mozilla, Microsoft,have decided to trust these public CAs ans they put these root certificates on every system that they distribute.










##4. Common Types of SSL Certificates
###2 Certificates that chain to the root
mac:  
####01:17  
keychain access->certificate assitant->evaluate a certificate







##5. Using Certificates
###1 Creating a demo certificate authority
openssl.cnf
```
dir =./groundswell
```
####06:25
```
cd groundswell
mkdir certs &&mkdir req &&mkdir newcerts &&mkdir private
echo "01" > serial && touch index.txt
```

###2 Generating a server certificate
```
openssl req -new -x509 -newkey rsa:2048 -keyout private/cakey.pem -out cacert.pem -days 365
```

###3 Installing your certificate on a client system
In the last step we created our certificate authority. In this step we're going to create the certificate and the certificate signing request. 
```
openssl req -new -nodes -newkey rsa:1024 -keyout private/ke.key -out req.ke.req -days 1095
```













##6. Check Your Expiration Dates
###2 Revoking a certificate
####01:03
```
openssl cs -revoke ../ke.pem
```

###3 Setting up a certificate-revocation list
```
cd /System/Library/OpenSSL
```
edit
```
vim openssl.cnf
```
comment out
```
#crlnumber = 
```
then
```
cd groundswell
mkdir crl
```
####02:06
```
openssl ca -config openssl.cnf -gencrl -out groundswell/crl/crl.pem
```
###4 Renewing a certificate
```
openssl req -new -new -nodes -out /System/Library/OpenSSL/groundswell/req/ke.req
```
So this next part is going to approve and sign the request and generate a new certificate that is not revoked. 
```
openssl ca -config /System/Library/OpenSSL/openssl.cnf -policy policy_anythind -out /System/Library/OpenSSL/groundswell/certs/ke.pem -infiles /System/Library/OpenSSL/groundswell/req/ke.req
```




##7. Protexting your
###2 Archiving in a secure and recoverable way




