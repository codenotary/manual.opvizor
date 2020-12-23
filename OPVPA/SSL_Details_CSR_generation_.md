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

  

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[image2018-7-17\_9-20-42.png](attachments/842301441/842301444.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-6-18\_17-1-44.png](attachments/842301441/842301447.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-4-16\_15-20-39.png](attachments/842301441/842301450.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-3-2\_20-12-27.png](attachments/842301441/842301453.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-4\_16-10-37.png](attachments/842301441/842301456.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-4\_16-9-10.png](attachments/842301441/842301459.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-10-30.png](attachments/842301441/842301462.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-4-58.png](attachments/842301441/842301465.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-3-7.png](attachments/842301441/842301468.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[vcenter\_level.png](attachments/842301441/842301471.png) (image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-28\_21-35-2.png](attachments/842301441/842301474.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-5-32.png](attachments/842301441/842301477.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-4-24.png](attachments/842301441/842301480.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-3-31.png](attachments/842301441/842301483.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav07481bb2ca03400983bd638b67b60558.png](attachments/842301441/842301486.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav1f04558543a7ec0ca05486a1f0e696a6.png](attachments/842301441/842301489.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavb3763aa4a64e94e607ca19d533ae443d.png](attachments/842301441/842301492.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav5be4bf5119573609c4923f11cbbbc51e.png](attachments/842301441/842301495.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav06dbff2300c14185a21435067a9e145e.png](attachments/842301441/842301498.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav69edf648f8ac183a0d6f9a7f661a0121.png](attachments/842301441/842301501.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddave52c19dbcac1b26312a64327f40f3d06.png](attachments/842301441/842301504.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav27122057d65ad1c538ca7ad517e64f95.png](attachments/842301441/842301507.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav092530424e35250521b7bda65c12d8b5.png](attachments/842301441/842301510.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav98988c63e221df9f9ddb93988e378246.png](attachments/842301441/842301513.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav54449f81ca6fd53d57b7cbf87cd26366.png](attachments/842301441/842301516.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavc2d3573add9776304d9bed5bc58a9064.png](attachments/842301441/842301519.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav638a05df1dbcdee1ddba6139af48bd39.png](attachments/842301441/842301522.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavac0142df730012f5f4afb8f014e9c2fe.png](attachments/842301441/842301525.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav18b203bd4133ce3a6bedf43320bb0d24.png](attachments/842301441/842301528.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav080aa4baa5f37f458a02ec468b813744.png](attachments/842301441/842301531.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav62fdac44032e5cc95b6320955873116c.png](attachments/842301441/842301534.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav3f2d004ecccb300e075f3a1676fc60ab.png](attachments/842301441/842301537.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddaveee8413b8437fab67605dadd0faa34c0.png](attachments/842301441/842301540.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavaa104f22ba852b4270fb90ccac8d4dee.png](attachments/842301441/842301543.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav61904dbc25a6cd35000b7cb7469627a1.png](attachments/842301441/842301546.png)
(image/png)  

</div>
