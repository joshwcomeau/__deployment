In case I ever need to set up a new One Ring droplet, I'm recording all
steps taken.

1) Purchase a droplet. Ubuntu 14.04 (or whatever's current in the future)
2) Add your SSH key to it, and access it with `ssh root@dropletIP`
3) Create a new user on the server to do deploy stuff.
    Call it `deploy` for convention.
    More info: https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04
3) Install Node.js with NVM (https://www.digitalocean.com/community/tutorials/how-to-install-node-js-with-nvm-node-version-manager-on-a-vps)
    Use a more recent version! 0.30+
    Copy a global version to /usr/local/bin/node
4) Install nginx
    Be sure to set server_names_hash_bucket_size to 64.
    More info: https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-12-04-lts-precise-pangolin

5) Ensure PM2 is installed globally for the deploy user

General info on multi-hosting:
https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-14-04


#### That's about it for the overall droplet!

Instructions for adding a new project to the droplet:

1) Set up a reverse proxy with nginx
    Make a file for the new domain (eg. nano /etc/nginx/conf.d/requestkittens.com.conf)
    This tells nginx to forward all traffic received for that domain to
    the port specified.

2) Get a database plan
    eg. Login to mongolab, create a new mongodb.

3) SSH in and create a config file under /home/deploy/config/PROJECT/production.json

4) Create a flightplan for the project
