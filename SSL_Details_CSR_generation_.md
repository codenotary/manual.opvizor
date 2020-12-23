# SSL Details (CSR generation)

<div class="toc-macro rbtoc1606556355824">

  - [Enable HTTPS](#SSLDetails\(CSRgeneration\)-EnableHTTPS)
  - [Create your own CSR](#SSLDetails\(CSRgeneration\)-CreateyourownCSR)

</div>

# Enable HTTPS

We made it pretty straightforward to enable HTTPS (SSL) to access the
appliance. Within the Admin interface / Overview click the Open Button
under SSL settings:

![](attachments/842301441/842301459.png?height=250)

Then either use the integrated SSL Certificate or upload your own PEM
formatted certificate.

![](attachments/842301441/842301456.png?height=250)

You can save the SSL Settings and decide to redirect all HTTP
connections to HTTPS as well.

# Create your own CSR

To create your own Certificate Signing Request, you can either use the
Performance Analyzer appliance or any other system with openssl
installed.

Login using the admin user (admin:VMware123) and select 1 to access the
shell.

<div class="code panel pdl" style="border-width: 1px;">

<div class="codeHeader panelHeader pdl" style="border-bottom-width: 1px;">

**Create CSR**

</div>

<div class="codeContent panelContent pdl">

``` bash
admin@opvperf:~$ umask 077
admin@opvperf:~$ mkdir cert
admin@opvperf:~$ cd cert
admin@opvperf:~/cert$ openssl req -new -newkey rsa:2048 -nodes -keyout opvperf.example.org.key -out opvperf.example.org.csr
Generating a 2048 bit RSA private key
............+++
..................................................+++
writing new private key to 'opvperf.example.org.key'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:US
State or Province Name (full name) [Some-State]:Texas
Locality Name (eg, city) []: Houston
Organization Name (eg, company) [Internet Widgits Pty Ltd]:opvizor, Inc
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []: opvperf.example.org
Email Address []:

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
admin@opvperf:~/cert$ ls -al
total 16
drwx------ 2 admin admin 4096 Oct 26 17:21 .
drwxr-xr-x 8 admin admin 4096 Oct 26 17:21 ..
-rw------- 1 admin admin 1001 Oct 26 17:21 opvperf.example.org.csr
-rw------- 1 admin admin 1704 Oct 26 17:21 opvperf.example.org.key
admin@opvperf:~/cert$ 
```

</div>

</div>

  

In detail:

1.  umask limits the access to the files to the current user.
2.  Create cert folder and change into it
3.  openssl creates a new RSA-Key (2048 bit) and a CSR for the
    Certificate Authority. You just need to fill in the details
    according to your needs. Most important is the Common Name (CN), the
    full network name, Performance Analyzer will be opened in the
    browser, i. e. opvperf.example.org.
4.  Important: if you chose a challenge password (default is none), you
    will need to type it into the Performance Analyzer appliance console
    after every reboot. There is also a restart required whenever you
    change the certificate key of the appliance.
5.  The .key-file will be kept secret on your system and the .csr-file
    will be send to the CA (this will be a manual step using scp if the
    generation happens locally on the Performance Analyzer appliance).

You will receive a certificate including the certificate chain from the
CA, either in separate files or all-in-one-file. Performance Analyzer
expects a certificate and the certificate chain in a PEM-encoded. The
PEM-file separates the different blocks of each certificate:

\-----BEGIN CERTIFICATE-----  
(Server SSL Certificate: content opvperf.example.org.crt)  
\-----END CERTIFICATE-----  
\-----BEGIN CERTIFICATE-----  
(Intermediate-Certificate: content certChainCA.crt)  
\-----END CERTIFICATE----  
  

If you received multiple certificate files from the CA, please copy them
together:

admin@opvperf:\~/cert$ **cp opvperf.example.org.crt
opvperf.example.org.fullChain.crt**  
admin@opvperf:\~/cert$ **cat certChainCA.crt \>\>
opvperf.example.org.fullChain.crt**

Using the Admin-UI (as shown in the beginning of this article) you can
load the content of the opvperf.example.org.key file as well as the
certificates file i.e. opvperf.example.org.fullChain.crt 

  
