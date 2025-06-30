Linux chmod Cheat Sheet
Alapvető jogosultságok (számokkal)
SzámJogosultságLeírás0---Nincs jogosultság1--xCsak futtatás2-w-Csak írás3-wxÍrás + futtatás4r--Csak olvasás5r-xOlvasás + futtatás6rw-Olvasás + írás7rwxTeljes jogosultság
Gyakori chmod értékek
chmodJogosultságTípusHasználat644rw-r--r--FájlNormál fájlok (tulajdonos írhat, mások olvashatnak)755rwxr-xr-xFájl/MappaFuttatható fájlok, mappák777rwxrwxrwxFájl/MappaTeljes jogosultság mindenkinek ⚠️600rw-------FájlPrivát fájlok (csak tulajdonos)700rwx------MappaPrivát mappa (csak tulajdonos)666rw-rw-rw-FájlMindenki írhat/olvashat744rwxr--r--FájlFuttatható, mások csak olvashatnak664rw-rw-r--FájlCsoport írhat, mások olvashatnak
Speciális jogosultságok
chmodJogosultságLeírás4755rwsr-xr-xSUID bit (futtatás tulajdonos jogaival)2755rwxr-sr-xSGID bit (futtatás csoport jogaival)1755rwxr-xr-tSticky bit (csak tulajdonos törölheti)
Betűs parancsok
ParancsJelentésPéldau+xTulajdonos futtatási jogchmod u+x fájlg-wCsoport írási jog elvételechmod g-w fájlo+rMások olvasási jogchmod o+r fájla+xMindenkinek futtatási jogchmod a+x fájlu=rwxTulajdonos jogok beállításachmod u=rwx fájl
Valós gyakorlati példák
644 (rw-r--r--) - Normál dokumentumok
bash# Szöveges fájlok, konfigurációk
chmod 644 ~/.bashrc
chmod 644 /etc/hosts
chmod 644 README.md
chmod 644 config.txt
chmod 644 /var/log/apache2/access.log
chmod 644 index.html
chmod 644 style.css
chmod 644 database.sql
755 (rwxr-xr-x) - Futtatható fájlok és mappák
bash# Scriptek és programok
chmod 755 /usr/local/bin/backup.sh
chmod 755 install.sh
chmod 755 /home/user/bin/mytool
chmod 755 /etc/init.d/apache2

# Mappák (böngészhetőség)
chmod 755 /var/www/html/
chmod 755 /home/user/Documents/
chmod 755 /opt/myapp/
chmod 755 /usr/local/share/
777 (rwxrwxrwx) - Teljes jogosultság ⚠️
bash# Ideiglenes mappák (CSAK SZÜKSÉG ESETÉN!)
chmod 777 /tmp/upload/
chmod 777 /var/tmp/cache/
chmod 777 /tmp/shared/

# Fejlesztési környezet log mappák
chmod 777 /var/log/debug/
chmod 777 /app/storage/logs/

# ⚠️ FIGYELEM: Biztonsági kockázat! Kerüld, ha lehet!
600 (rw-------) - Privát, érzékeny fájlok
bash# SSH kulcsok
chmod 600 ~/.ssh/id_rsa
chmod 600 ~/.ssh/id_ed25519
chmod 600 ~/.ssh/config

# Adatbázis jelszavak, konfigurációk
chmod 600 /etc/mysql/my.cnf
chmod 600 ~/.my.cnf
chmod 600 /etc/shadow
chmod 600 ~/.netrc

# API kulcsok, tanúsítványok
chmod 600 /etc/ssl/private/server.key
chmod 600 ~/.aws/credentials
chmod 600 /etc/openvpn/server.key
chmod 600 backup_passwords.txt
700 (rwx------) - Privát mappák
bash# Személyes mappák
chmod 700 ~/.ssh/
chmod 700 ~/.gnupg/
chmod 700 ~/private/
chmod 700 ~/.config/

# Rendszer mappák
chmod 700 /root/
chmod 700 /var/lib/mysql/
chmod 700 /etc/ssl/private/
chmod 700 /home/user/.cache/

# Backup mappák
chmod 700 /backup/sensitive/
chmod 700 ~/Documents/passwords/
További gyakori példák
bash# Webszerver beállítások
chmod 644 /var/www/html/*.html          # HTML fájlok
chmod 644 /var/www/html/*.css           # CSS fájlok  
chmod 755 /var/www/html/cgi-bin/        # CGI mappa
chmod 755 /var/www/html/images/         # Képek mappája

# Git repository
chmod 644 .gitignore
chmod 755 .git/
chmod 600 ~/.ssh/id_rsa                 # Git SSH kulcs

# Cron jobek
chmod 755 /etc/cron.daily/backup
chmod 644 /etc/crontab
chmod 700 /var/spool/cron/crontabs/

# Log fájlok
chmod 644 /var/log/syslog
chmod 600 /var/log/auth.log             # Érzékeny auth logok
chmod 755 /var/log/                     # Log mappa
