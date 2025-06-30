# Linux chmod Cheat Sheet

## Alapvető jogosultságok (számokkal)

| Szám | Jogosultság | Leírás |
|------|-------------|---------|
| 0 | --- | Nincs jogosultság |
| 1 | --x | Csak futtatás |
| 2 | -w- | Csak írás |
| 3 | -wx | Írás + futtatás |
| 4 | r-- | Csak olvasás |
| 5 | r-x | Olvasás + futtatás |
| 6 | rw- | Olvasás + írás |
| 7 | rwx | Teljes jogosultság |

## Gyakori chmod értékek

| chmod | Jogosultság | Típus | Használat |
|-------|-------------|--------|-----------|
| 644 | rw-r--r-- | Fájl | Normál fájlok (tulajdonos írhat, mások olvashatnak) |
| 755 | rwxr-xr-x | Fájl/Mappa | Futtatható fájlok, mappák |
| 777 | rwxrwxrwx | Fájl/Mappa | Teljes jogosultság mindenkinek ⚠️ |
| 600 | rw------- | Fájl | Privát fájlok (csak tulajdonos) |
| 700 | rwx------ | Mappa | Privát mappa (csak tulajdonos) |
| 666 | rw-rw-rw- | Fájl | Mindenki írhat/olvashat |
| 744 | rwxr--r-- | Fájl | Futtatható, mások csak olvashatnak |
| 664 | rw-rw-r-- | Fájl | Csoport írhat, mások olvashatnak |

## Speciális jogosultságok

| chmod | Jogosultság | Leírás |
|-------|-------------|---------|
| 4755 | rwsr-xr-x | SUID bit (futtatás tulajdonos jogaival) |
| 2755 | rwxr-sr-x | SGID bit (futtatás csoport jogaival) |
| 1755 | rwxr-xr-t | Sticky bit (csak tulajdonos törölheti) |

## Betűs parancsok

| Parancs | Jelentés | Példa |
|---------|----------|--------|
| u+x | Tulajdonos futtatási jog | `chmod u+x fájl` |
| g-w | Csoport írási jog elvétele | `chmod g-w fájl` |
| o+r | Mások olvasási jog | `chmod o+r fájl` |
| a+x | Mindenkinek futtatási jog | `chmod a+x fájl` |
| u=rwx | Tulajdonos jogok beállítása | `chmod u=rwx fájl` |

## Valós gyakorlati példák

### 644 (rw-r--r--) - Normál dokumentumok
```bash
# Szöveges fájlok, konfigurációk
chmod 644 ~/.bashrc
chmod 644 /etc/hosts
chmod 644 README.md
chmod 644 config.txt
chmod 644 /var/log/apache2/access.log
chmod 644 index.html
chmod 644 style.css
chmod 644 database.sql
```

### 755 (rwxr-xr-x) - Futtatható fájlok és mappák
```bash
# Scriptek és programok
chmod 755 /usr/local/bin/backup.sh
chmod 755 install.sh
chmod 755 /home/user/bin/mytool
chmod 755 /etc/init.d/apache2

# Mappák (böngészhetőség)
chmod 755 /var/www/html/
chmod 755 /home/user/Documents/
chmod 755 /opt/myapp/
chmod 755 /usr/local/share/
```

### 777 (rwxrwxrwx) - Teljes jogosultság ⚠️
```bash
# Ideiglenes mappák (CSAK SZÜKSÉG ESETÉN!)
chmod 777 /tmp/upload/
chmod 777 /var/tmp/cache/
chmod 777 /tmp/shared/

# Fejlesztési környezet log mappák
chmod 777 /var/log/debug/
chmod 777 /app/storage/logs/

# ⚠️ FIGYELEM: Biztonsági kockázat! Kerüld, ha lehet!
```

### 600 (rw-------) - Privát, érzékeny fájlok
```bash
# SSH kulcsok
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
```

### 700 (rwx------) - Privát mappák
```bash
# Személyes mappák
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
```

## További gyakori példák

```bash
# Webszerver beállítások
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
```

## Jogosultság ellenőrzése

```bash
# Részletes lista jogosultságokkal
ls -l

# Csak jogosultságok megjelenítése
stat -c %a fájlnév
```

## Emlékeztető

- **Első szám**: Tulajdonos (user) jogai
- **Második szám**: Csoport (group) jogai  
- **Harmadik szám**: Mások (others) jogai
- **r=4, w=2, x=1** - összeadva kapjuk a végső számot
