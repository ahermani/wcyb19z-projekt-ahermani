# EVM - lvl 1
 Wyniki skanowania nmap pokazują nam, że na maszynie otwarte są porty 22, 53, 80, 110, 139, 143, 445.
 
 ![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/nmap.png)
 
 Wykorzystałam fakt otwartego portu 80 z usługą http i stronę Apache, wpisując IP EVM w przeglądarce. Na stronie zobaczyć można było komunikat:
 
 ![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/apache.png)
 
 Według wskazówki należało więc poszukać katalogu `wordpress`. Użyłam do tego narzędzia `DIRB`, które przeszukuje metodą brute-force zawartość stron internetowych i serwerów.
 
 ![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/dirb.png)
 
DIRB znalazł wspomniany wyżej folder. W celu zdobycia więcej informacji wykorzystałam kolejne nowe narzędzie Kali Linuxa: `WPScan`, które służy właśnie do skanowania WordPress pod względem podatności.

Użyłam komendy do wypisania motywów (at - themes), wtyczek (ap - plugin) oraz użytkowników (u - user) zalogowanych na stronie:
```
wpscan --url http://192.168.10.103/wordpress -e at -e ap -e u 
```

Skaner znalazł 1 nazwę użytkownika:

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/wpscan_user.png)

Złamałam hasło użytkownika metodą brute force, z wykorzystaniem słownika rockyou.txt. Użyłam komendy: 
```
wpscan --url http://192.168.10.103/wordpress -U c0rrupt3d_brain -P /usr/share/wordlists/rockyou.txt
```
I uzyskałam hasło do logowania: 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/wpscan_password.png)

W metasploicie użyłam exploita `exploit/unix/webapp/wp_admin_shell_upload`, który zapewnia poświadczenia admina. Ustawiłam opcje:
* PASSWORD 24992499
* RHOSTS 192.168.10.103
* TARGETURI /wordpress
* USERNAME c0rrupt3d_brain

Uzyskałam dostęp do maszyny.

W folderze root3r znajdował się plik `.root_password_ssh.txt`, który zawierał hasło do roota: `willy26`.

![image]()

Stworzyłam powłokę i w meterpreterze wpisałam polecenie w celu zwiększenia uprawnień:
```
python -c 'import pty; pty.spawn("/bin/bash")'
```
I zalogowałam się do roota, poleceniem `su root` oraz hasłem `willy26`.

Flaga znajdowała się w folderze root w pliku `proof.txt`.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/flag.png)
