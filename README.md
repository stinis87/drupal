For oppstart av Drupal 8 docker containere med prekonfigurert profil

1. git clone https://github.com/stinis87/drupal.git
2. I prosjektet kjøres kommandoen "docker-compose up -d"
3. Kjør composer install kommando
3. Naviger til http:drupaldocker:8000
4. Kjør site install og velg profilen "bouvet"
5. For å endre på hvilke versjon av php, mariadb/mysql, nginx/apache osv benyttes .evn filen. Docker bildet og container må bygges op startes opp på nytt.

