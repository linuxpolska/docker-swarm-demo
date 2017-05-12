# Orkiestracja kontenerów z Docker Swarm i Compose - insrukcja uczestnika

- [Zaloguj się na host swarm master w swoim klastrze](#logowanie)
- [Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#weryfikacja-klaster)
- [Uruchom usługę Wordpress w klastrze](#usluga-uruchomienie)
- [Z poziomu klastra sprawdź czy usługa działa](#usluga-weryfikacja-klaster)
- [Sprawdź czy usługa jest dostępna w internecie](#usluga-weryfikacja-internet)
- [Wyskaluj usługę Wordpress](#usluga-skalowanie)
- [Usuń usługę](#usluga-usuniecie)


## Zaloguj się na host swarm master w swoim klastrze <a id='logowanie'/>
Każdemu uczestnikowi został przydzielony unikatowy numer, który należy wpisać w adresie domenowym hosta swarm master.

- FQDN:
  - Uczestnicy nr. 01-24: sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  - Uczestnicy nr. 25-50: sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- Klucz prywatny: swarm_master
- Login: sdcuser


<div id='weryfikacja-klaster'/>

## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne 

```
docker node list
```



## Uruchom usługę Wordpress w klastrze <a id="usluga-uruchomienie"/>

1. Na Swarm masterze załóż katalog na projekt (nazwa może być dowona) i skopiuj do niego plik docker-compose.yml
2. W katalogu projektu stwtórz dwa pliki:
   1. db_passswd.txt - plik 
   2. wordrpes.txt - sfas

