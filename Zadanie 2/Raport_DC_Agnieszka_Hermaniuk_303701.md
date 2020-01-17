# DC - lvl1

Skanowanie nmap wykazało, że host ma otwarte porty 22, 11, 34890 oraz 80, na którym działa Apache 2.2 i Drupal 7. 

Strona wyglądała następująco:

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/drupal_site.PNG)

Skorzystłam z kolejnego nowego dla mnie narzędzia penetracyjnego: `droopescan`, który służy do skanowania w celu znajdowania problemów z CMS i dotyczy m.in. Drupala. 

Skan przeprowadziłam komendą:
```
droopescan scan drupal -u http://192.168.10.104/
```

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/droopescan.png)

Wyszukanie exploita do prawdopodobnej wersji Drupala (7) wykazało, że mamy do czynienia z podatnością `Drupalgeddon`, która dotyczy wersji Drupala starszych niż 7.32.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/searchsploit_drupal.png)

Następnie poszukałam exploita na podatność Drupalgeddon w metasploicie.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/exploit_drupalgeddon.png)

Ustawiłam opcje:
* RHOSTS 192.168.10.104

I uzyskałam dostęp do maszyny z powłoką meterpreter. Następnie stworzyłam interaktywną powłokę.
```
shell
python -c "import pty;pty.spawn('/bin/bash')"
```
Po otawrciu zawartości bieżącego katalogu okazało się, że znajduje się w nim 1. flaga:

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/flag1.PNG)

Zawierała wskazówkę odnośnie pliku konfiguracyjnego Drupala. Znajduje się on pod ścieżką: `/var/www/sites/default/settings.php`. Otworzyłam ten plik.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/flag2.PNG)

Była w nim 2. flaga, która zawierała dane uwierzytelniające do bazdy danych MySQL.

Zalogowałam się do bazy danych. Użyłam komendy: `mysql -u dbuser -p` i wpisałam hasło użytkownika dbuser.

Następnie wyświetliłam bazy danych poleceniem: `show databases;`. Określiłam, jakiej z nich używam: `use drupaldb;` i wyświetliłam wszystkie tablice w bazie danych: `show tables;`. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/sql_commands.PNG)

Flaga 3 znajdowała się ostatecznie w tablicy `field_data_body`.
```
describe field_data_body; 
select body_value from field_data_body;
```
![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/flag3.PNG)

I kierowała ona do pliku `/etc/passwd`.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/etc_passwd.PNG)

Jak widać, jednym z użytkowników jest `flag4`. Przeszłam do jego folderu, gdzie znajdowała się flaga 4.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/flag4.PNG)

Następnie użyłam linuxowych poleceń eskalacji uprawnień.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/privilege_escalation1.png)

Przy pomocy funkcji find można teraz wyświetlić zawartość katalogu `root`

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/find_root.png)

Znajduje się w nim plik o nazwie `thefinalflag.txt`. Można go otworzyć specjalnym poleceniem i przeczytać zawartość ostatniej flagi:
```
find /root/thefinalflag.txt -exec cat {} \;
```

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/finalflag.png)





