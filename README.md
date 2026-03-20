RFC 08032022 
December 15, 2025
 ***** RFC08032022 *****



The TLS 1.3 is not always correctly implemented on the DNS Public Key Infrastructure (PKI). We can replace it by the state-of-the-art Wireguard. There are several aspects to consider in the DNS:



1. The concentration of risk in a PKI

2. The generation of domain names certificates

3. The storage of domain names certificates

4. The access to domain names certificates

5. The DNS requests and answers

6. The access to the Web ressources

7. The DNS servers information



1.The DNS PKI has several levels and concentrates risk on very few root Certification Authorities (CAs). Also, it is said that some root certificates private keys have leaked. We shall use only one level to reduce risk. Indeed, absolute root CAs shall be seen as the top of the DNS PKI pyramid.



https://cpl.thalesgroup.com/faq/public-key-infrastructure-pki/what-certification-authority-or-root-private-key-theft



Also, it appears clearly that websites providing information about compromising electromagnetic signals have disappeared from the web.



https://www.ssi.gouv.fr/uploads/IMG/pdf/II300_tempest_anssi.pdf



https://mindcontrolfrance.blogspot.com



2.The domain name owner shall generate its own Wireguard key pair with wg for each domain and subdomain. The domain name owner shall create a certificate file containing the domain name of its website and the public key generated with wg according to the following standard: column 1: domain name, column 2: public key. The domain name owner shall then self-sign with PGP the certificate file with the same private key he generated with wg.



3.Domain name owners shall post the certificate file for each of their domains and subdomains on several IPs along with their PGP public key. Domain name owners shall publish their PGP public key at least on the websites corresponding to their domain names. Domain name owners can put their Wireguard public key in a standard WHOIS section and in a DNS record for example. Redundancy and integrity verifications shall be automated and certificates shall be propagated automatically to all IPs.



4.The browser shall be connected via Wireguard tunnels to the IPs where certificates are posted. Browser developers would then avoid storage of certificates in the browser. In other words, each domain name owner shall be its own Certificate Authority. Domain names can still be sold the same way.



5.Wireguard can be used for DNS requests.



6.When the user visits a website, the browser shall look for the domain or subdomain Wireguard public key in the WHOIS, in a DNS record and in one or several of the IPs where the certificates are stored. The browser shall then connect through a Wireguard tunnel to the ressource address answered by the DNS server if the public key corresponds to the domain name of the website after checking the WHOIS, the DNS record and the IPs where the certificates are stored.



7.SDNS can connect all non-zombie DNS servers together until this project is deployed.



https://sdns.dev/



Example:



Write an Arch Linux install script with the following packages:



Prepare the Arch Linux VM file, the VM will host the key server described above for redundancy speed increase in case of successful attacks:



If there are enough physical machines deployed for fast enough integrity checks, the following VPS setup will not be rejected by the pool:



Deploy a Linux OS in the VPS:



Harden the Linux OS for security:



Setup a public folder in the VPS:



Setup a script to only allow upload of files with a defined format in the public folder:



Setup a Wireguard server in the VPS:



Setup a Wireguard client:



Setup a Wireguard tunnel between your Wireguard client and Wireguard server:



Setup scripts to migrate the VPS to other available servers automatically:



Generate a Wireguard key pair: umask 077 && wg genkey > privkey



Derive the public key from it: cat privkey | wg pubkey > pubkey



Generate a certificate file: echo "domainname.xyz" | cat - pubkey > certificate.file



Generate a PGP keypair with RSA state of the art bit length key, according to the Cyber Knights Templars, maybe more than 64k: https://alt.security.pgp.narkive.com/BXVOpAKJ/how-to-generate-longer-even-32768-bit-long-key-with-gpg



Export public PGP key: gpg -a --export KEYID > public.asc



Export private PGP key: gpg -a --export-secret-key KEYID > private.asc



Sign and encrypt the certificate file: gpg --encrypt --sign --armor -r cplanat@danstachatte.xyz certificate.file



Upload your certificate file to an IP through a Wireguard tunnel: curl...



Upload your PGP public key to an IP through a Wireguard tunnel: curl...



Sources:



https://www.instagram.com/p/CgRoJDNNxm_/?igshid=ZjhmMmE0MjU=



https://security.stackexchange.com/questions/87564/how-does-ssl-tls-pki-work



https://www.wireguard.com/quickstart/



https://www.scaleway.com/en/docs/tutorials/install-wireguard/



https://www.reddit.com/r/WireGuard/comments/d8iidj/wireguard_as_a_replacement_for_dns_over_tls/



https://doc.turris.cz/doc/en/public/wireguard



https://superuser.com/questions/1285136/cat-command-and-echo



https://askubuntu.com/questions/679230/how-to-sign-files-with-ubuntu-command-line-tools-and-my-own-keys



https://gock.net/blog/2020/gpg-cheat-sheet/



https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key



https://gist.github.com/amingilani/8ccb1e1422800d4d9a31
