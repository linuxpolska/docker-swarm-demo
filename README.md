# Orkiestracja kontenerów z Docker Swarm i Compose - instrukcja dla uczestnika

- [Zaloguj się na host swarm master w swoim klastrze](#logowanie)
- [Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#weryfikacja-klaster)
- [Uruchom usługę Wordpress w klastrze](#usluga-uruchomienie)
- [Z poziomu klastra sprawdź czy usługa działa](#usluga-weryfikacja-klaster)
- [Sprawdź czy usługa jest dostępna w internecie](#usluga-weryfikacja-internet)
- [Wyskaluj usługę Wordpress](#usluga-skalowanie)
- [Usuń usługę](#usluga-usuniecie)


## Zaloguj się na host swarm master w swoim klastrze <a id='logowanie'/>

Do logowania użyj klucza prywatnego.

Plik klucza i informacje potrzebne do zalogowania się na hoście swarm master w Twoim klastrze:

- FQDN:
  - Uczestnicy nr. 01-24: sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  - Uczestnicy nr. 25-50: sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- [Klucz prywatny](https://raw.githubusercontent.com/linuxpolska/docker-swarm-demo/master/swarm_master) (hasło zostanie przekazane przez instruktora)
- Login: sdcuser



## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne <a id="weryfikacja-klaster"/>
Wyświetl informacje o wszystkich nodach w Twoim klastrze; wykonaj komendę.

```
docker node list
```

## Uruchom usługę Wordpress w klastrze <a id="usluga-uruchomienie"/>

1. Na hoście swarm master załóż katalog na projekt (nazwa może być dowolna) i skopiuj do niego plik [docker-compose.yml](https://raw.githubusercontent.com/linuxpolska/docker-swarm-demo/master/docker-compose.yml).
    ```
    wget https://raw.githubusercontent.com/linuxpolska/docker-swarm-demo/master/docker-compose.yml
    ```
2. W katalogu projektu utwórz dwa pliki:
   - db_root_password.txt - plik z hasłem do konta root do bazy danych
   - db_password.txt - plik z hasłem do konta wordpress do bazy danych
4. Uruchom usługę w klastrze wydając komendę
    ```
    docker stack deploy --compose-file docker-compose.yml wordpress
    ```
## Sprawdź czy usługa została uruchomiona na klastrze
```
docker service list
```
```
docker service ps wordpress
```
```
docker service inspect
```
```
docker service logs wordpress_web
docker service logs wordpress_db
```


## Sprawdź czy serwis wordpress jest dostępny w Internecie
Otwórz w przeglądarce główną stronę wordpresa uruchomionego na Twoim klastrze. Główna strona Twojej usługi jest dostępna pod adresem: 
- Uczestnicy nr. 01-24: http:\/\/sdclab\<NUMER\>.eastus2.cloudapp.azure.com
- Uczestnicy nr. 25-50: http:\/\/sdclab\<NUMER\>.eastus.cloudapp.azure.com

Zainicjalizuj usługę wordpress korzystając z jej interface webowego.

## Wyskaluj aplikację wordpress_web
Uruchom dodatkową instancję aplikacji wordpres_web na kolejnym workerze w Twoim klastrze.
```
docker service scale wordpress_web=2
```
Sprawdź czy instancja została uruchomiona w klastrze
```
docker service ps wordpress_web
````
```
docker service ps wordpress_web
```

## Usuń usługę wordpress
```
docker stack rm wordpress
```
