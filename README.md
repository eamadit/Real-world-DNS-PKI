# Real-world-DNS-PKI
I can regularly observe TLS 1.3 secured website duplications. The attacker indicates its presence by slight modifications on the web page. The website of the IETF does not accept draft submission because of an error indicating problems with unicode glyphes, which appears to be a simulated error after long verifications of each glyphe on the submitted text file. Supposedly, the IETF website hacker indicates its presence this way. I would like interested people to help me on the following project, cynically named RFC08032022. This work shall be governed by an Apache License 2.0 interpreted under French law.

***** RFC08032022 *****

https://github.com/eamadit/

https://github.com/eamadit/Real-world-DNS-PKI/blob/main/README.md

Good Day,

I can regularly observe TLS 1.3 secured website duplications. The attacker indicates its presence by slight modifications on the web page. In particular, I obseved this on the two following web pages:

https://en.wikipedia.org/wiki/Henry_Kissinger the colors were inverted on this attack which has been observed in Orange France ADSL networks: https://www.instagram.com/p/ChP_bPhNlOa/?igshid=MDJmNzVkMjY=

https://legacktem.com/ the font of the main page is changed on this attack which can be observed on tor exit nodes and in Orange France ADSL networks, the attack is documented there: https://legacktem.com/blog-english/wp-content/uploads/2022/08/IMG_1296.mov
https://www.instagram.com/tv/CgwYd_glulw/?igshid=NmZiMzY2Mjc=
I was not able to verify the website IP address aside from the wordpress comment IP origin.

https://haxf4rall.com/2021/10/23/forgecert-golden-certificates/

https://cybernews.com/resources/what-is-a-dns-attack/

https://www.darknet.org.uk/2011/02/mallory-transparent-tcp-udp-proxy/

The website of the IETF does not accept draft submission because of an error indicating problems with unicode glyphes, which appears to be a simulated error after long verifications of each glyphe on the submitted text file. Supposedly, the IETF website hacker indicates its presence this way.

I would like interested people to help me on the following project, cynically named RFC08032022:

***** RFC08032022 *****

The TLS 1.3 is not always correctly implemented on the DNS PKI. We shall replace it by the state-of-the-art Wiregard. There is several aspects to consider in the DNS:

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

2.The domain name owner shall generate its own Wireguard key pair with wg for each domain and subdomain. The domain name owner shall create a certificate file containing the domain name of its website and the public key generated with wg according to the following standard: column 1: domain name, column 2: public key. The domain name owner shall then self-sign with PGP the certificate file with the same private key he generated with wg.

3.Domain name owners shall post the certificate file for each of their domains and subdomains on several IPs along with their PGP public key. Domain name owners shall publish their PGP public key at least on the websites corresponding to their domain names. Domain name owners shall put their Wireguard public key in a standard WHOIS section and in a TLSA record. Redundancy and integrity verifications shall be automated and certificates shall be propagated automatically to all IPs.

4.The browser shall be connected via Wireguard tunnels to the IPs where certificates are posted. Browser developers would then avoid storage of certificates in the browser. In other words, each domain name owner shall be its own CA. Domain names shall still be sold the same way. The Wireguard public key shall be seen in a standard WHOIS section and in a TLSA record.

5.Wireguard shall replace DoT and DoH for DNS requests.

6.When the user visits a website, the browser shall look for the domain or subdomain Wireguard public key in the WHOIS, a TLSA record and in one or several of the IPs where the certificates are stored. The browser shall then connect through a Wireguard tunnel to the ressource address answered by the DNS server if the public key corresponds to the domain name of the website after checking the WHOIS, the TLSA record and the IPs where the certificates are stored.

7.SDNS shall connect all non-zombie DNS servers together until this project is deployed.

Example:

Setup a VPS:

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
