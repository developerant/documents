"The requested apache plugin does not appear to be installed"
sudo apt-get install python-certbot-apache

One domain only
```certbot --apache certonly -d domain1.com```



certbot --apache certonly -n -d domain1.com


--dry-run


--apache for apache server, use --nginx flag for nginx server
-n option execute the command without prompt
-d domain1.com to execute only for domain1.com


certbot --apache -d solero.sfclients.com --dry-run



"Mailgun\Model\Message\SendResponse Object
(
    [id:Mailgun\Model\Message\SendResponse:private] => <20190130011033.1.5F102616FC105D57@sandbox93ab65b61e9044648b59b481421e8007.mailgun.org>
    [message:Mailgun\Model\Message\SendResponse:private] => Queued. Thank you.
)
"