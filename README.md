## Docked-Passbolt
### Dockerized Passbolt Password Manager with Traefik Security (SSL)
<br>


## How to Install

1. Install docker on the server
```
sudo apt install docker.io docker-compose -y
```

2. Clone the repository
```
https://github.com/ZhiyamRRC/Docked-Passbolt.git
```

3. Edit the "docker-compose-ce.yaml" and change Followings with server dns;
    - APP_FULL_BASE_URL: https://passbolt.local
    - traefik.http.routers.passbolt-http.rule: "Host(`passbolt.domain.tld`)
    - traefik.http.routers.passbolt-https.rule: "Host(`passbolt.domain.tld`)

4. Edit the "terefik.yaml" and change Followings;
    - email: yourname@domain.tld

5. Deploy the Containers
```
docker-compose -f docker-compose-ce.yaml up -d
```

6. Create first Admin User; Use following command and eplace Email, First and Last Name according to you.
```
$ docker-compose -f docker-compose-ce.yaml exec passbolt su -m -c "/usr/share/php/passbolt/bin/cake \
                                passbolt register_user \
                                -u <your@email.com> \
                                -f <yourname> \
                                -l <surname> \
                                -r admin" -s /bin/sh www-data
```

7. Use the URL to access the Passbolt manager;
    - Install the browser extension.
    - Create a strong password for Admin User.
    - Make sure to download the recovery kit.
    - Pick a color and 3 letters as a security consern.
<br>

#### Extra Commands
To enter editor mode
```
nano <your-file-name>
```

To cheak the running containers
```
docker ps
```
<br>


## Credits

- Docker Documentation - https://help.passbolt.com/hosting/install/ce/docker
- Terefik Documentation - https://help.passbolt.com/configure/https/ce/docker/auto.html
- Network Chuck Demo - https://youtu.be/jAfQvMxcokI
