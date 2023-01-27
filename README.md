> Simply way to run your POS project locally

- add new folder call it: `_docker` from GIT <>
- add to root all folders from project pos
- if project not in root  `$mosConfig_pos = '';` need to change name folder
- change name `configuration.example.php` to `configuration.php`
- prescribe the data (in the configuration file) of the database according to the example:  
`docker-compose.yml -> mysql`

> RUN docker
- open terminal 
- go to docker: `cd _docker`
- run command `docker-compose up -d`

Wait until the docker's containers are loaded

> How to use
- go to `localhost:8000`
- provide `user_id` from DB and press: `ENTER`
- enjoy developing...

> Xdebug configuration

Install for chrome: Xdebug helper
- Change settings IDE key
  Select your IDE to use the default sessionkey or choose other to use a custom key.
- PhpStorm -> PHPSTORM

Images in folder `docs`

- Open `Settings` -> `PHP` -> Button `...` (image 1,2)
- Button `+` -> `From Docker...` (image 3)
- Press `Docker` -> Choose: `docker-php` (image 4)
- Check if correct Xdebug version, PHP version press: `Apply` (image 5)
- Edit docker container path: change `/opt/project` to `/var/www/html` (images 6,7)
- Go to PHP -> DBGp Proxy
- change port to `9000` and IDE key to `PHPSTORM` (image 8)
- Go to PHP -> Servers
- Press `+` and add new server:
- `Name: server` 
- `Host: localhost`
- `Port: 80`
- `src` -> `/var/www/html` (images 9,10)

