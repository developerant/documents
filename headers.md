# Response Headers

## Header to configure CORS vulnerability fix
Header set Access-Control-Allow-Origin: domain.com
Header set Acess-Control-Allow-Methods: "GET, HEAD, POST"

## Header configuration to prevent 'click-jacking'
Header set X-FRAME-OPTIONS "SAMEORIGIN"

## Header configuration to prevent sending system information to web browsers
Header unset X-Powered-By

## Apache force downloading of images
```<FilesMatch "\.(gif|jpe?g|png)$">
	ForceType application/octet-stream
	Header set Content-Disposition attachment
</FilesMatch>```