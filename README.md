For oppstart av Drupal 8 docker containere med prekonfigurert profil

1. git clone https://github.com/stinis87/drupal.git

2. I prosjektet kjøres kommandoen "docker-compose up -d" (Dersom du ikke ønsker å benytte docker kjører du istede bare composer install)

3. Logg inn på i container med "docker exec -it 'container name' /bin/bash" hvor container name er id til woodyby/drupal-php. Kjør composer install kommando

4. Logg inn i node container med "docker-compose run node sh" og kjøre "npm install" derifra.

5. Kjør "npm run gulp watch" for å følge med endringer i sass filer.

6. Naviger til http:drupaldocker:8000

7. Kjør site install og velg profilen "bouvet"

8. Velg "drupal" på det meste av settings borsett fra hostname som skal være service name for databaseserver, by default "mariadb".

9. Naviger til siden for konfigurering av filsystem og sett opp mappe for temp filer og "clear cache".

10. For å endre på hvilke versjon av php, mariadb/mysql, nginx/apache osv benyttes .evn filen. Docker bildet og container må bygges op startes opp på nytt.

11. NB: HUSK Å FJERNE!!!!!!!
  "stinis87/bouvet_theme": "dev-master",
  "stinis87/bouvet_utils": "dev-master",
fra composer.json filen slik at den ikke overskrives når man igjen kjører composer install senere.

12. For å aktivere xdebug, fjern utkommentering av følgende i docker.compose.yml:
  PHP_XDEBUG: 1
  PHP_XDEBUG_DEFAULT_ENABLE: 1
  PHP_XDEBUG_REMOTE_CONNECT_BACK: 0
  PHP_XDEBUG_REMOTE_ENABLE: 1
  PHP_IDE_CONFIG: serverName=my-ide
  PHP_XDEBUG_REMOTE_HOST: host.docker.internal # Docker 18.03+ & Linux/Mac/Win
 
 13. Dersom du ønsker å bruke xdebug i phpstorm:
 
  Open > Edit Configurations from the main menu, choose Defaults > PHP Web Page in the left sidebar
  Click to [...] to the right of Server and add a new server
  Enter name "my-ide" (as specified in PHP_IDE_CONFIG)
  Enter any host, it does not matter
  Check Use path mappings, select path to your project and enter /var/www/html/web in the right column (Absolute path on the server)
  Choose newly created server in "Server" for PHP Web Page
  Save settings
