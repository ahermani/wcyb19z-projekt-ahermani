Security Onion posiada wiele narzędzi, tj.:
* Elasticsearch
* Logstash
* Kibana
* Snort
* Suricata
* Zeek
* Sguil
* Squert<br>
Umożliwiają one dogłębną analizę plików PCAP zawierających ruch sieciowy ataków na system. W Security Onion znajduje się folder z przykładowymi testowymi plikami PCAP.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/onion_test_pcaps.PNG)

## Plik 1.
Zaimportowałam plik 2014-12-18-Nuclear-EK-traffic.pcap.<br>

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/import.PNG)

Otorzyłam Kibanę i zmieniłam czas na timestamp zaimportowanych pakietów. W sekcji Dashboard widać, że Kibana pobrała nowe logi. Można też odczytać, z jakich narzędzi NSM te logi pochodzą.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/sensors.PNG)

W tym przypadku Kibana otrzymała logi głównie ze Snorta oraz Bro (typy: http - analiza zapytań http, files - analiza plików i conn - szczegóły połączeń IP, TCP, UDP i ICMP).<br>

Następnie otworzyłam narzędzie `Squert` do wyświetlenia alertów. Squert ułatwia poznanie kontekstu rozpatrywanych alertów dzięki możliwości przejrzenia ich metadanych i szeregów czasowych. W sekcji `EVENTS` znajduje się lista wszystkich znalezionych eventów.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/events.PNG)

W zakładce `SUMMARY` znajduje sie procentowa rozpiska sygnatur, portów, adresów IP źródłowego i docelowego ruchu sieciowego.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/summary.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/summary_ports.PNG)

Sekcja `VIEWS` pokazuje Sankey Diagram, który przedstawia zależność między adresami IP uczestniczącymi w ruchu sieciowym. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/views.PNG)

Hostem uczestniczącym w każdym połączeniu jest tutaj 192.168.204.137 (zainfekowany).<br> Logi Squerta można filtrować ze względu na adresy IP. W ten sposób można ustalić, że host 93.190.48.4 odpowiedzialny był za przekierowanie połączenia na Landing Page Server. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/redirect.PNG)

Z kolei host 178.62.255.107 był źródłem payloadu wykorzystującego nieaktualną wtyczkę Flash oraz Exploit Kita pobranego na zainfekowanego hosta.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/source%20of%20ek.PNG)

Alert o tym znaczeniu możemy także zobaczyć w Kibanie, jego źródłem jest Snort.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/payload_kibana.PNG)

Na końcu zainfekowany host łączy się z 176.9.159.141 (dane IP występuje w ruchu sieciowym tylko ten jeden raz, może to być CnC).

Powróciwszy do Kibany można dodatkowo przefiltrować zebrane logi, np. znajdując geolokalizację ostatniego IP.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/checkin%20dest.PNG)


## Plik 2.
Zaimportowałam plik zeus-sample-1.pcap.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/zeus_import.PNG)

Otworzyłam Kibanę, ustawiając odpowiednią datę.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/kibana_sensors.PNG)

Oprócz poprzednich typów logów pojawiły się także `bro_weird` - wykrywa anomalie oraz `bro_pe` - do plików Portable Executable.

Squert pokazał następujące alerty:

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squert_all.PNG)

Oraz podsumowanie adresów IP, sygnatur i portów:

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/zeus_ips.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/zeus_ports.PNG)

Tak natomiast wyglądały połączenia pomiędzy hostami

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/zeus_sankey_diagram.PNG)

Po filtrowaniu wyników ze względu na IP można było wywnioskować, że zainfekowanym hostem jest 192.168.3.35, który pobrał Zbota od hosta 188.124.9.56. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/delivery.PNG)

W narzędziu `Sguil` po wygenerowaniu transkryptu można zobaczyć też nazwę strony, z której pobrano złośliwy plik.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/get_seus.PNG)

Z tego samego hosta załadawany został następnie payload.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/exploitation.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/payload%20and%20exe%20download.PNG)

Następnie nasz host wszedł na stronę przekierowującą na Sutra TDS, czyli system służący do przekierowywania ruchu hosta w sieci.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/sutra%20redirect.PNG)

Hostem odpowiedzialnym za przekierowania był 65.254.40.251. W Sguilu można zobaczyć nazwy przekierowywanych stron.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/red1.PNG)
![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/red2.PNG)

Na koniec nastąpiło połączenie z CnC (188.124.5.100)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/cnc.PNG)

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/cnc_file.PNG)

