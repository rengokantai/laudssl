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
