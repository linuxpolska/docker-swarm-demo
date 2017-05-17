# Orkiestracja kontenerów z Docker Swarm i Compose - instrukcja dla uczestnika

- [Zaloguj się na host swarm manager w swoim klastrze](#logowanie)
- [Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#weryfikacja-klaster)
- [Uruchom usługę Wordpress w klastrze](#usluga-uruchomienie)
- [Z poziomu klastra sprawdź czy usługa działa](#usluga-weryfikacja-klaster)
- [Sprawdź czy usługa jest dostępna w internecie](#usluga-weryfikacja-internet)
- [Wyskaluj usługę Wordpress](#usluga-skalowanie)
- [Usuń usługę](#usluga-usuniecie)


## Zaloguj się na host swarm manager w swoim klastrze <a id='logowanie'/>

Do logowania użyj klucza prywatnego.

Plik klucza i informacje potrzebne do zalogowania się na hoście swarm manager  w Twoim klastrze:

- FQDN:
  - Uczestnicy nr. 01-26: sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  - Uczestnicy nr. 27-50: sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- [Klucz prywatny](https://www.dropbox.com/s/cup7vwtbvy8whqs/swarm_master_key?dl=0) Dostęp do klucza oraz sam klucz są zabezpieczone hasłami, które zostaną przekazane przez instruktora w trakcie warsztatów.
- Login: sdcuser



## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne <a id="weryfikacja-klaster"/>
Wyświetl informacje o wszystkich nodach w Twoim klastrze; wykonaj komendę.

```
docker node list
```

## Uruchom usługę Wordpress w klastrze <a id="usluga-uruchomienie"/>

1. Na hoście swarm manager załóż katalog na projekt (nazwa może być dowolna) i skopiuj do niego plik [docker-compose.yml](https://raw.githubusercontent.com/linuxpolska/docker-swarm-demo/master/docker-compose.yml).
    ```
    wget https://raw.githubusercontent.com/linuxpolska/docker-swarm-demo/master/docker-compose.yml
    ```
2. W katalogu projektu utwórz:
   - db_root_password.txt - plik z hasłem do konta root do bazy danych
    ```
    echo tajnehaslo1 > db_root_password.txt
    ```
   - db_password.txt - plik z hasłem do konta wordpress do bazy danych
    ```
    echo tajnehaslo2 > db_password.txt
    ```

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

Zainicjalizuj serwis.

## Wyskaluj aplikację wordpress_web
Uruchom dodatkową instancję aplikacji wordpres_web na kolejnym workerze w Twoim klastrze.
```
docker service scale wordpress_web=2
```

Sprawdź czy instancja została uruchomiona w klastrze
```
docker service ps wordpress_web
```
```
docker service list
```

## Usuń usługę wordpress
```
docker stack rm wordpress
```
