# DC - lvl1

Skanowanie nmap wykazało, że host ma otwarte porty 22, 11, 34890 oraz 80, na którym działa Apache 2.2 i Drupal 7. Można więc skorzystać z kolejnego nowego dla mnie narzędzia penetracyjnego: `droopescan`, który służy do skanowania w celu znajdowania problemów z CMS i dotyczy m.in. Drupala. 

Skan przeprowadziłam komendą:
```
droopescan scan drupal -u http://192.168.10.104/
```

![image]()

Na podstawie możliwych wersji Drupala (7.22-7.26) można wywnioskować, że mamy do czynienia ze znaną podatnością `Drupageddon`, którą odkryto w wersjach Drupala starszych niż 7.32.

Potwierdziło się to po wyszukaniu exploita do Drupala 7.

![image]()

Następnie poszukałam exploita na podatność Drupageddon w metasploicie.

![image]()

Ustawiłam opcje:
* RHOSTS 192.168.10.104

I uzyskałam dostęp do maszyny z powłoką meterpreter. Następnie użyłam poleceń, zwiększających moje uprawnienia.
```

```
