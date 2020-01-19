# Raport OSINT, organizacja: Politechnika Gdańska

# Agnieszka Hermaniuk, nr albumu 303701, e-mail: 01149363@pw.edu.pl

## GEOLOKALIZACJA IP (wynik ze strony iplocation.net)
IP: 153.19.40.70<br>
Kraj: Poland<br>
Region: Pomorskie<br>
Miasto: Gdańsk<br>
Szerokość geo.: 54.3731<br>
Długość geo.: 18.6187

## INFRASTRUKTURA SIECI
Wyniki poleceń:
```
host -t ns pg.edu.pl
host -t mx pg.edu.pl
```
Serwery:
  * ns1.pg.gda.pl		153.19.40.230
	* Szerokość geo.: 54.3731
  	* Długość geo.: 18.6187
  * ns2.pg.gda.pl		153.19.40.229
  	* Szerokość geo.: 54.3731
  	* Długość geo.: 18.6187
  * ns2.task.gda.pl	212.77.96.123
  	* Szerokość geo.: 52.2376
  	* Długość geo.: 21.0160

mail: 5 smtp.pg.edu.pl

## RESTART SERWERÓW

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/reboot.PNG)

## PROBLEMY Z BEZPIECZEŃSTWEM

### Wiadomości
* 30.03.2012 - opublikowanie przez Anonymous baz danych wydziałów PG (Studenckiego Klubu Turystycznego Politechniki Gdańskiej, Wydziału Architektury Politechniki Gdańskiej, witrynie Katedry Chemii Nieorganicznej Politechniki Gdańskiej)
* 2018 - wyniki egzaminów na stronie profesora pojawiały się publicznie wraz z nazwiskami uczniów (obecnie można znaleźć sporo wyników egzaminów wraz z nazwiskami i imionami studentów, np. [plik1](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/Fizyka_molekularna_C_25.02.2016.pdf), [plik2](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/Fizyka_molekularna_wyniki%20sesja%20podstawowa.pdf))
* 2019 - defraudacja pieniędzy z kasy zapomogowo-pożyczkowej (pół miliona zł)
* 2019 - problemy z działaniem poczty elektronicznej

## Podatności

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan7.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan8.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan9.PNG)

## USŁUGI SERWERÓW

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan4.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan5.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/pg.eduscan6.PNG)

## SUBDOMENY
Znalezione przy użyciu narzędzi: `theHarvester` (wykorzystałam źródła: google, virustotal, threatcrowd, crtsh i netcraft) oraz `dnsenum`, a następnie scalone, posortowane i przefiltrowane ze względu na duplikaty.

adonis-prod-app1.pg.edu.pl.

akademiki.pg.edu.pl

ankieta.pg.edu.pl

ankiety.pg.edu.pl

arch.pg.edu.pl

bg.pg.edu.pl

bilety.pg.edu.pl

biuletyn.pg.edu.pl

budzetobywatelski.pg.edu.pl

campus.pg.edu.pl

cdn.pg.edu.pl

center.pg.edu.pl

chat.pg.edu.pl

chat.szkol.pg.edu.pl

chem.pg.edu.pl

chor.pg.edu.pl

cjo.pg.edu.pl

clickmeeting.pg.edu.pl

cmtm.pg.edu.pl

cnm.pg.edu.pl

cnm-srv.pg.edu.pl

csa.pg.edu.pl

ctwit-crm.pg.edu.pl

ctwt.pg.edu.pl

cui.pg.edu.pl

cui-prod-nas01.pg.edu.pl

dav.webmail.pg.edu.pl

domki.pg.edu.pl

drive.pg.edu.pl

dzp.pg.edu.pl

eclipse.eti.pg.edu.pl

ects.pg.edu.pl

eduroam.pg.edu.pl

eia.pg.edu.pl

eka.pg.edu.pl

enauczanie.pg.edu.pl

eti.pg.edu.pl

ext.webmail.pg.edu.pl

ezd.pg.edu.pl

ezd-prod-app1.pg.edu.pl

ezd-prod-db1.pg.edu.pl

ezd-proxy.szkol.pg.edu.pl

ezd-static.szkol.pg.edu.pl

ezd.szkol.pg.edu.pl

faks.pg.edu.pl

fax.pg.edu.pl

festiwal.pg.edu.pl

forum.pg.edu.pl

ftims.pg.edu.pl

git.pg.edu.pl

han.bg.pg.edu.pl

help.pg.edu.pl

imap.eti.pg.edu.pl

imap.pg.edu.pl

imap.student.pg.edu.pl

imap.zie.pg.edu.pl

kampus.pg.edu.pl

katalog.bg.pg.edu.pl

kube-prod-front1.pg.edu.pl.

kube-prod-front2.pg.edu.pl.

kube-prod-front3.pg.edu.pl.

kube-prod-front4.pg.edu.pl.

kube-prod-http.pg.edu.pl

login.han.bg.pg.edu.pl

logowanie.pg.edu.pl

logowanie.szkol.pg.edu.pl

mail.eti.pg.edu.pl

mail.zie.pg.edu.pl

mba.pg.edu.pl

mech.pg.edu.pl

media.pg.edu.pl

mediateka.cjo.pg.edu.pl

meteo.pg.edu.pl

mobile.pg.edu.pl

moja.pg.edu.pl

moja.szkol.pg.edu.pl

mx.zie.pg.edu.pl

my.pg.edu.pl

oio.pg.edu.pl

pg.edu.pl

pg.moja.pg.edu.pl

pg.moja.szkol.pg.edu.pl

phplist.pg.edu.pl

platnosci.pg.edu.pl

platnosci.test.pg.edu.pl

poczta.eti.pg.edu.pl

poczta.pg.edu.pl

pomoc.pg.edu.pl

pop3.zie.pg.edu.pl

position.pg.edu.pl.

praca.pg.edu.pl

rekrutacja.awf.pg.edu.pl

rekrutacja.pg.edu.pl

repos.pg.edu.pl

roundcube.pg.edu.pl

samorzad.pg.edu.pl

sis.eti.pg.edu.pl

sklep.pg.edu.pl

sk.pg.edu.pl

smtp.eti.pg.edu.pl

smtplist.pg.edu.pl

smtp.pg.edu.pl

smtprelay.mailing.pg.edu.pl

smtp.student.pg.edu.pl

smtp.zie.pg.edu.pl

spotkania.pg.edu.pl

student.pg.edu.pl

techem9.pg.edu.pl

vcenter.cui.pg.edu.pl

vcenter.pg.edu.pl

vcenter.ucs.pg.edu.pl

voip.pg.edu.pl

vpn1.pg.edu.pl

vpn2.pg.edu.pl

vpn.pg.edu.pl

webapps.pg.edu.pl

webinar.pg.edu.pl

webmail.pg.edu.pl

wew.moja.szkol.pg.edu.pl

wilis.pg.edu.pl

zadania.pg.edu.pl

zapisy.pg.edu.pl

zgloszenia.pg.edu.pl

zie.pg.edu.pl

zlecenia.pg.edu.pl



## CACHE GOOGLE
Wyszukiwanie z dn.:: 6.01.2020 12:43<br>
Wynikiem jest wyświetlenie z dn: 5.01.2020 5:18:40

## DANE KONTAKTOWE
**Adres:**

Politechnika Gdańska<br>
ul. Gabriela Narutowicza 11/12<br>
80-233 Gdańsk<br>
Polska<br>
NIP: 5840203593, REGON: 000001620

**Informacja o numerach telefonów w Politechnice Gdańskiej**

tel.: +48 58 347 11 00 

**Informacja o pracownikach**

Można wyszukać imię, nazwisko, stanowisko, wydział i nr telefonu każdego pracownika: https://moja.pg.edu.pl/app/addressBook/

**Informacja o rekrutacji**

pon.–pt. 7.30–15.30<br>
tel.: +48 58 348 67 00<br>
https://pg.edu.pl/rekrutacja<br>
rekrutacja@pg.edu.pl

**Kontakt dla mediów**

tel.: +48 58 347 29 99<br>
biuro.prasowe@pg.edu.pl

**Webmaster**

tel.: +48 58 348 63 37<br>
webmaster@pg.edu.pl

Przydatne mogą się też okazać:
* [wykaz jednostek uczestniczących w postępowaniu przetargowym](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/Za%C5%82%C4%85cznik%20nr%202%20-%20wykaz%20jednostek.pdf) - wraz z danymi osób do konatktu
* [wykaz osób upoważnionych do składania zleceń](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%201/Osoby%20upowa%C5%BCnione%20do%20sk%C5%82adania%20zlece%C5%84.pdf)

Dodatkowo przy użyciu narzędzia `theHarvester` źródło LinkedIn znalazło 3 użytkowników: Anatolii Tyshchenko, Jakub Śledź, Jan Pieczykolan. Google znalazł 8 maili: 
* annwnuk@pg.edu.pl
* bartlomiej.mroz@pg.edu.pl
* blorb@pg.edu.pl
* krzysztof.grzelec@pg.edu.pl
* lech.michalski@pg.edu.pl
* malinowska-panczyk@pg.edu.pl
* plorb@pg.edu.pl
* rekrutacja@pg.edu.pl
