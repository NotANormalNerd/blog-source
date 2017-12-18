How to create a valid TLS Certificate
#####################################

:date: 2015-02-04 13:37
:tags: tls, security, 
:slug: tls-certificate
:summary: How to get a free TLS certfifcate for your webserver. And why it is important to get such a certificate.

As you already have noticed, or even better you haven't, your are reading this over a secured and encrypted connection. 
If you click on that small lock right beside the url, you will see more information about your connection.

What does that mean for you?
----------------------------

For you it means that even if you are sitting in an internet cafe with a unprotected wifi connection, nobody will be able to read what you are doing.
On a blog like that, it's not that important, but when you are logging into your online banking account or even your facebook account, it gets important.
If your connection is not encrypted and secured, everyone between you and the server can read your password and steal your identity.

That is why a lot of services like google, facebook, youtube and so on have already changed their settings, to only allow encrypted connections.

Getting an account at StartSSL and verifing your domain
-------------------------------------------------------
Okay. Now you have a webserver yourself? You want to offer a encrypted and secured connection to your visitors? Or just want to annoy the NSA? Perfect.

First of you need the following things:
 * a website, douhhhh
 * a domain, for simplicity
 * access to the webserver configuration
 * access to one of these mail addresses on your server

  * hostmaster@example.com
  * webmaster@example.com
  * postmaster@example.com
  * There seem to be some other options in special cases

First of we need to get a certificate. For that we use StartSSL Services, as they offer free basic certificates that fulfill the purpose of encrypting connections without alerting the user.
For that we go to StartSSL_ and sign up for a account. For that you should use your real name and address, as they could check that information.

You will get an email with an activiation link and a code. Insert the code on the page and wait for them to verify your account. After they verified your account, 
they generate a client certificate to logon to the StartSSL homepage again. This will be saved to you browser and you should also export that and back it up somewhere save.

After that you will be in the control center. Click on the **Validation Wizard** tab on the main site and choose **Domain Name Validation**. Enter the domain on the next site.
Make sure to leave out any subdomain, like *www* or *mail* or something. Go to the next site and choose one of the mail addresses to send the verification mail to. 
If you can't validate yourself as authorized you can not create a certificate. With this step you verfiy that you control the server and the domain, for which the certificates will be issued.

After you got the verification mail, it is time to take the next step. You now have the ability to create a free certificate for every subdomain you need. 
You will have to do the following steps for every subdomain on its own.

Creating the certificate and getting it signed
----------------------------------------------
Now that your domain has been verified, go to the **certification wizard** and choose **Web Server TLS/SSL Certificate**. 
****IMPORTANT**** skip the next step, to avoid generating an insecure private key. ****IMPORTANT****

The following steps should work with all linux systems:

.. code::
 
	openssl genrsa -aes256 -out mysite_secure.key 2048
	openssl req -new -sha256 -key mysite_secure.key -out mysite.csr

The first line creates a private rsa key for us. It has a bitlength of 2048 what is currently considered secure for normal applications.
Use 4096 for webshops or other kind of authentication requiring application. Give the key a string password.

The second line creates a new certificate signing request (csr). It will be signed with the key we just created and will have a sha512 hash.
You can skip all the questions given by the openssl programm, since all metadata will be ignored by StartSSL.

Now we take the csr file open it and copy the whole file content into the text area on the StartSSL page. After pressing continue there will be another information page.
Read it and press next. Now the certificate will be generated. Copy the complete text area context in a mysite.pem and save the file.

You will need another certificate file called sub.class1.server.sha2.ca.pem. You will find the file on a ftp server of startssl.com via google. This is the intermediate certificate,
that StartSSL used to sign your request. We need to deliver the cetficate since it is not delivered by browsers. Most browser only contain the StartSSL Root certificate that was used
to sign the intermediate certificate. This is called a web of trust. Browser trust the root, which trusts the intermediate, which trusts us.

In the following step we need to create a public key from our private key. Therefore we do the following steps:

.. code::
	
	openssl rsa -in mysite_secure.key -out mysite.key
	cat mysite.pem ../sub.class1.server.sha2.ca.pem > mysite-chain.pem

The first line in this example creates the public key from our private key for our webserver. The second copies the intermediate certificate 
and our certificate into a common file, which will be delivered to webclients accessing the server.

Installing it to our webserver
------------------------------

After that we can give the public key file and the certificate file to our webserver, which in my case in a nginx webserver.
You will find lots of other instruction how to do this on various other webserver in the internet.

.. code::
	
	ssl_certificate         /path/to/cert/mysite-chain.pem;
	ssl_certificate_key     /path/to/key/mysite.key;

Add the above two lines to your nginx site configuration and enable ssl ports of the webserver.
Enable other security features like HTST for enhanced security. You can find further information on that in the interwebs.

Restart the server and access your webserver. Your browser should now show a locked lock in the url bar. This means your site is secured and you are a trusted website for your browser.

Now you can provide your visitors a bit more security and annoy the NSA a little bit.

Further steps now include thightening your webserver security. You can check that on the SSLLabs_ Website.

.. _StartSSL: https://www.startssl.com/?app=12
.. _SSLLabs: https://www.ssllabs.com
