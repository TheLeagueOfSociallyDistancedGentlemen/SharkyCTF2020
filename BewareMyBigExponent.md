Beware My Big Exponent
1. Exported certificate from TLS handshake in Wireshark
2. Ran openssl against file:
  openssl x509 -inform DER -in ~/Downloads/certificate.der -text
Certificate shows unusually large exponent:
----
Exponent:
                    00:92:cb:d9:20:05:56:3d:ae:d0:6c:4b:01:0f:bc:
                    53:dd:98:c6:37:11:da:d7:b4:71:2b:ad:8b:a6:be:
                    c3:8a:ce:7f:3e:f4:8e:49:1c:88:e4:6f:38:b4:b3:
                    c4:43:d6:80:99:76:83:8f:dd:aa:02:37:24:04:5c:
                    f0:42:b2:13:25:be:66:93:98:40:06:8b:56:9a:73:
                    66:ce:c0:13:ce:ec:fe:9d:3b:63:b6:81:7b:cf:e6:
                    d1:4d:72:a8:69:92:18:98:80:aa:13:92:37:36:6d:
                    d7:6b:19:7a:d1:30:ae:c9:80:60:56:e7:55:b6:c7:
                    ea:97:c4:12:dc:82:26:8c:f6:cb:95:b6:87:49:77:
                    8b:79:e6:76:d8:df:ea:67:f7:9b:eb:f9:50:b1:18:
                    d6:1a:ca:71:8e:57:64:44:62:65:90:71:c2:ee:f9:
                    a7:5f:bf:2d:6f:ea:2d:54:b4:c6:58:65:15:68:a9:
                    58:ee:9c:2a:c1:54:2f:0b:02:a0:07:87:af:1e:cf:
                    bc:f8:b5:ca:c1:f2:f3:42:15:fe:af:67:4c:55:ea:
                    b4:f9:d2:89:fc:fa:09:89:47:af:3c:17:e1:e1:ae:
                    a3:f0:28:ca:07:7c:a3:5b:82:19:95:30:1f:fd:e7:
                    13:36:4d:9a:ac:9a:3c:9e:e4:81:a8:fc:b5:d5:98:
                    b6:c1
----
3. Exported .pub key from Cer using OpenSSL
4. Attempted RSA CTF Tool brute force but no success:
 python ./RsaCtfTool.py --publickey ~/Downloads/key.pub --verbose --private 
[*] Performing hastads attack.
[*] Performing factordb attack.
[*] Performing pastctfprimes attack.
[*] Loaded 71 primes
[*] Performing noveltyprimes attack.
[*] Performing smallq attack.
[*] Performing wiener attack.
[*] Performing comfact_cn attack.
[*] Performing fermat attack.
[*] Performing siqs attack.
[*] Warning: Modulus too large for SIQS attack module

Thats as far as I got    
                
