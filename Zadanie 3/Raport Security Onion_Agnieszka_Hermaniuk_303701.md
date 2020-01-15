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
Zaimportowałam plik fake_av.pcap.<br>

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/fake_av.PNG)

Następnie otworzyłam narzędzie `Squert` do wyświetlenia alertów. Squert ułatwia poznanie kontekstu rozpatrywanych alertów dzięki możliwości przejrzenia ich metadanych i szeregów czasowych. W sekcji `EVENTS` znajduje się lista wszystkich znalezionych eventów.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squert_event_view.PNG)

W zakładce `SUMMARY` znajduje sie procentowa rozpiska sygnatur oraz adresów IP źródłowego i docelowego ruchu sieciowego.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squert_summary.PNG)

Łatwo zauważyć, że w pliku z przechwyconego pakietu aktywny jest Command and Control Trojan. Z analizy adresów IP widać, że ruch pochodzi z adresu 172.16.150.20 (prawdopodobnie zainfekowany host), który najprawdopodobniej komunikuje się z adresem 58.64.132.141 (CnC). 

Sekcja `VIEWS` pokazuje Sankey Diagram, który przedstawia zależność między adresami IP uczestniczącymi w ruchu sieciowym. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squert_views.PNG)

Zdecydowanie najwięcej linii łączy 172.16.150.20 z 58.64.132.141. Dodatkowo source adres łączy się także z adresem 66.32.119.38 (jedna czerwona linia).

Z powrotem w sekcji `EVENTS` można przefiltrować wyniki po adresie IP 66.32.119.38. Z logów widać, że z tego adresu pobrano podejrzany plik z rozszerzeniem .doc.exe.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/filter_ip.PNG)

Następnie przeszłam do narzędzia `Squil`.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squil.PNG)

I stworzyłam zapytanie dla IP 66.32.119.38. 

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squil_query.PNG)

Wygenerowałam transkrypcję dla pierwszego alertu o pobraniu podejrzanego pliku.

![image](https://github.com/wcyb19z-lab/wcyb19z-projekt-ahermani/blob/screenshots/Zadanie%203/squil_transcript.PNG)

Można tu zobaczyć nazwę niebezpiecznego pliku.

Na tym etapie możliwa jest też ekstrakcja pliku przy wykorzystaniu Wiresharka lub NetworkMiner w celu dalszej analizy.

## Plik 2.
