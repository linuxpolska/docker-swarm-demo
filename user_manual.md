# Orkiestracja kontenerów z Docker Swarm i Compose - insrukcja uczestnika

1. [Zaloguj się na host swarm master w swoim klastrze](#logowanie)
2. [Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#weryfikacja-klaster)
3. [Uruchom usługę Wordpress w klastrze](#usluga-uruchomienie)

<a id='logowanie'/>
## Zaloguj się na host swarm master w swoim klastrze

- FQDN: 
  ​	Uczestnicy nr. 01-24: 
  ​		sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  ​	Uczestnicy nr. 25-50: 	
  ​		sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- Klucz prywatny: swarm_master
- Login: sdcuser


<a id='weryfikacja-klaster'/>
## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne 

```
docker node list
```


<a id='usluga-uruchomienie'/>
## Uruchom usługę Wordpress w klastrze

1. Na Swarm masterze załóż katalog na projekt (nazwa może być dowona) i skopiuj do niego plik docker-compose.yml
2. W katalogu projektu stwtórz dwa pliki:
   1. db_passswd.txt - plik 
   2. wordrpes.txt - sfas

