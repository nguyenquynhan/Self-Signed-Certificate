# Create Self Signed Certificate
## What is a Self Signed Certificate?
 - A self-signed certificate is an SSL/TSL certificate not signed by a public or private certificate authority. Instead, it is signed by the creator’s own personal or root CA certificate.
 - For more detail, can you read [this artical](https://devopscube.com/create-self-signed-certificates-openssl), it also shows you step by step to create Self Signed Certificate.
## To be simpler, we can create Self Signed Certificate with a `ssl.sh` file, it's all in one file. How to do:
1. Run `./ssl.sh  yourhostname.com` 
	- NOTE: you should change `yourhostname.com` into yours
	- And run it on Git Bash or any CMD support openssl
2. After run it, it generated many files, you focus on 3 these files.
  <img width="531" alt="image" src="https://user-images.githubusercontent.com/8075534/195827294-915e0878-9e65-40b8-a99d-5da55fc5c97b.png">


3. You use `yourhostname.com.crt` and `yourhostname.com.key` to setup SSL for your server. Example with nginx:
  ```
  server {

  listen   443;

  ssl    on;
  ssl_certificate    /etc/ssl/yourhostname.com.crt;
  ssl_certificate_key    /etc/ssl/yourhostname.com.key;

  server_name your.domain.com;
  access_log /var/log/nginx/nginx.vhost.access.log;
  error_log /var/log/nginx/nginx.vhost.error.log;
  location / {
  root   /home/www/public_html/your.domain.com/public/;
  index  index.html;
  }

  }
  ```
4. Install Certificate Authority In Your Browser/OS
  - You need to install the `rootCA.crt` in your browser or operating system to avoid the security message that shows up in the browser when using self-signed certificates.
	  - [Adding certificate to chrome on Windows](https://docs.vmware.com/en/VMware-Adapter-for-SAP-Landscape-Management/2.1.0/Installation-and-Administration-Guide-for-VLA-Administrators/GUID-D60F08AD-6E54-4959-A272-458D08B8B038.html)
	  - [For MAC check this guide](https://support.apple.com/en-in/guide/keychain-access/kyca2431/mac)

## Agian, for more detail, please cam you read [this artical](https://devopscube.com/create-self-signed-certificates-openssl), it also shows you all. :) 
