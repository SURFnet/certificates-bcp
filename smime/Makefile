RCPT=billy.pilgrim@gmx.us
RCPT=jodi@surfnet.nl

default:

COMODORSAClientAuthenticationandSecureEmailCA.pem:
	wget --quiet --output-document - http://crt.comodoca.com/COMODORSAClientAuthenticationandSecureEmailCA.crt | openssl x509 -inform DER -outform PEM -out COMODORSAClientAuthenticationandSecureEmailCA.pem

COMODORSAAddTrustCA.pem:
	wget --quiet --output-document - http://crt.comodoca.com/COMODORSAAddTrustCA.crt | openssl x509 -inform DER -outform PEM -out COMODORSAAddTrustCA.pem

message:
	echo "Hello world!" > message

billy.pem: billy.p12
	openssl pkcs12 -nodes -in billy.p12 -out billy.pem

message.signed: message billy.pem COMODORSAClientAuthenticationandSecureEmailCA.pem
	openssl smime -sign -text -signer billy.pem -from billy.pilgrim@gmx.us -to ${RCPT} -subject "Signed message" -in message -out message.signed -certfile COMODORSAClientAuthenticationandSecureEmailCA.pem

verify: COMODORSAAddTrustCA.pem message.signed
	openssl smime -verify -in message.signed -CAfile COMODORSAAddTrustCA.pem 

send: message.signed
	/usr/sbin/ssmtp ${RCPT} < message.signed

clean:
	-rm COMODORSAClientAuthenticationandSecureEmailCA.pem COMODORSAAddTrustCA.pem message message.signed
realclean:
	-rm billy.pem
