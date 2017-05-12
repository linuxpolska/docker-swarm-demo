# Orkiestracja kontenerów z Docker Swarm i Compose - insrukcja uczestnika

[Zaloguj się na host swarm master w swoim klastrze](#Zaloguj się na host swarm master w swoim klastrze)
[Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne)
[Uruchom usługę Wordpress w klastrze](#Uruchom usługę Wordpress w klastrze)

   ​

## Zaloguj się na host swarm master w swoim klastrze

- FQDN: 
  ​	Uczestnicy nr. 01-24: 
  ​		sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  ​	Uczestnicy nr. 25-50: 	
  ​		sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- Klucz prywatny: swarm_master
- Login: sdcuser



## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne 

```
docker node list
```



## Uruchom usługę Wordpress w klastrze

1. Na Swarm masterze załóż katalog na projekt (nazwa może być dowona) i skopiuj do niego plik docker-compose.yml
2. W katalogu projektu stwtórz dwa pliki:
   1. db_passswd.txt - plik 
   2. wordrpes.txt - sfas

