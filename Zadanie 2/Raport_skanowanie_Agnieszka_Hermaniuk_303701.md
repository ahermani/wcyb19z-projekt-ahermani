Do zadania pobrałam podane maszyny i utworzyłam sieć wewnętrzną składającą się z nich oraz z Kali Linuxa.

```
netdiscover -ieth0
```

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/intnet.PNG)

Następnie przeskanowałam maszyny przed podejściem do testów penetracyjnych.

# Skanowanie `nmap`

Wyniki skanowania maszyn pod kątem detekcji OS, usług i ich wersji oraz otwartych portów.

## Kioptrix

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/Kioptrix/nmap_t4.png)


## DC

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/CD/nmap.png)

## EVM

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%202/EVM/nmap.png)

# Skanowanie podatności

## OpenVas
* [Kioptrix](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/openvas-kioptrix-scan.pdf)
* [DC](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/openvas-dc-scan.pdf)
* [EVM](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/openvas-evm-scan.pdf)

## Nessus
* [Kioptrix](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/nessus-kioptrix-scan.pdf)
* [DC](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/nessus-dc-scan.pdf)
* [EVM](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/master/Zadanie%202/nessus-evm-scan.pdf)
