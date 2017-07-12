# framadate-in-docker
Docker implementation of Framadate (Doodle open source equivalent)

## Build
docker build -t bastienf/framadate framadate/

## Deployment
1. Dependencies
  * Run mysql server:
  ```
  docker run --name mysql -e MYSQL_ROOT_PASSWORD=<some-password> -e MYSQL_DATABASE=framadateDB -d mysql:latest --sql-mode="ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
  ```

2. Deploy Framadate
  * With GUI install:
  ```
  docker run -d --name framadate --rm --link mysql:mysql -p 8080:80 bastienf/framadate
  ```

  * With existing config.php:
  ```
  docker run -d --name framadate --rm --link mysql:mysql -p 8080:80 -v <path_to_some>/config.php:/var/www/html/app/inc/config.php:ro bastienf/framadate
  ```
  Template for config.php: [link](https://raw.githubusercontent.com/BastienF/framadate/master/app/inc/config.template.php)

3. Misc
  * You can overwrite the php.ini file with option `-v <path_to_some>/php.ini:/var/www/html/:ro`
