## Digital Ocean

I use a [Digital Ocean][1] droplet to test this, currently an Ubuntu 14.04 with the LEMP stack application.

### Preparing the database and the Nginx config file

I've used [this guide][2]

### Restarting services

service php5-fpm restart
service nginx restart

## Audio Files

In order to test audio tracks in different qualities and formats, 
I am using the Creative Commons Licensed (Attribution Non-Commercial Share-Alike 3.0) tracks 
from the albums [Ghosts I - IV][3] and [The Slip][4] by Nine Inch Nails hosted by Archive.org

## Audio Files Upload

PHP comes with some small limits for upload and post size, here are the settings of php.ini that might need changing:

- upload_max_filesize
- post_max_size
- max_execution_time

Plus, Nginx may refuse requests with a large body

```
client intended to send too large body: 8489132 bytes, client: 187.66.94.116, server: , request: "POST /wp-admin/async-upload.php HTTP/1.1"
```

So edit the config to include in the server section this:

```
client_max_body_size 20M;
```

[1]: https://www.digitalocean.com/?refcode=2c0f8d80ba34  
[2]: https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-nginx-on-ubuntu-12-04
[3]: https://archive.org/details/nineinchnails_ghosts_I_IV
[4]: https://archive.org/details/NineInchNailsTheSlip24bit96khz
