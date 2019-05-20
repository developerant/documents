# Apache Commands

## Show modules
```apache2ctl -M``` or ```httpd -M```

## Reinstall
```bash
sudo apt-get --purge remove apache2
sudo apt-get autoremove
sudo apt-get install apache2
sudo /etc/init.d/apache2 restart
```

### Upgrade Apache

#### With apt-get
sudo apt-add-repository ppa:ondrej/apache2
sudo apt-get update
sudo apt-get dist-upgrade


## Bugs

### Debugging

```sudo service apache2 status```

### PHP Stopped working
```sudo a2dismod mpm_event && sudo a2enmod mpm_prefork && sudo a2enmod php7.0 && sudo service apache2 restart```


### "could not bind to address [::]:80"
Means port 80 is in use. Run:
```sudo netstat -tulpn | grep :80```

Look for process ID and name e.g. 4245/httpd

If httpd, for example (could be nginx or something else)
```ps aux | grep httpd```

Try to disable the process manually, if not:
```sudo kill -a httpd```
