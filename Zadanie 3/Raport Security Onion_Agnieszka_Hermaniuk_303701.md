Security Onionposiada wiele narzędzi, tj.:
* Elasticsearch
* Logstash
* Kibana
* Snort
* Suricata
* Zeek
* Sguil
* Squert
Umożliwiają one dogłębną analizę plików PCAP zawierających ruch sieciowy ataków na system. W Security Onion znajduje się folder z przykładowymi testowymi plikami PCAP.

![image]()

## Plik 1.
Zaimportowałam plik fake_av.pcap.<br>

![image]()

Następnie otworzyłam narzędzie `Squert` do wyświetlenia alertów. Squert ułatwia poznanie kontekstu rozpatrywanych alertów dzięki możliwości przejrzenia ich metadanych i szeregów czasowych. W sekcji `EVENTS` znajduje się lista wszystkich znalezionych eventów.

![image]()

W zakładce `SUMMARY` znajduje sie procentowa rozpiska sygnatur oraz adresów IP źródłowego i docelowego ruchu sieciowego.

![image]()

Łatwo zauważyć, że w pliku z przechwyconego pakietu aktywny jest Command and Control Trojan. Z analizy adresów IP widać, że ruch pochodzi z adresu 172.16.150.20 (prawdopodobnie zainfekowany host), który najprawdopodobniej komunikuje się z adresem 58.64.132.141 (CnC). 

Sekcja `VIEWS` pokazuje Sankey Diagram, który przedstawia zależność między adresami IP uczestniczącymi w ruchu sieciowym. 

![image]()

Zdecydowanie najwięcej linii łączy 172.16.150.20 z 58.64.132.141. Dodatkowo source adres łączy się także z adresem 66.32.119.38 (jedna czerwona linia).

Z powrotem w sekcji `EVENTS` można przefiltrować wyniki po adresie IP 66.32.119.38. Z logów widać, że z tego adresu pobrano podejrzany plik z rozszerzeniem .doc.exe.

![image]()

Następnie przeszłam do narzędzia `Squil`.

![image]()

I stworzyłam zapytanie dla IP 66.32.119.38. 

![image]()

Wygenerowałam transkrypcję dla pierwszego alertu o pobraniu podejrzanego pliku.

![image]()

Można tu zobaczyć nazwę niebezpiecznego pliku.

Na tym etapie możliwa jest też ekstrakcja pliku przy wykorzystaniu Wiresharka lub NetworkMiner w celu dalszej analizy.

## Plik 2.
