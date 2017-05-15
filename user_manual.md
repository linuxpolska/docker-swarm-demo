# Orkiestracja kontenerów z Docker Swarm i Compose - insrukcja uczestnika

- [Zaloguj się na host swarm master w swoim klastrze](#logowanie)
- [Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne](#weryfikacja-klaster)
- [Uruchom usługę Wordpress w klastrze](#usluga-uruchomienie)
- [Z poziomu klastra sprawdź czy usługa działa](#usluga-weryfikacja-klaster)
- [Sprawdź czy usługa jest dostępna w internecie](#usluga-weryfikacja-internet)
- [Wyskaluj usługę Wordpress](#usluga-skalowanie)
- [Usuń usługę](#usluga-usuniecie)


## Zaloguj się na host swarm master w swoim klastrze <a id='logowanie'/>
Każdemu uczestnikowi został przydzielony unikatowy numer, który należy wpisać w adresie domenowym hosta swarm master. Ponżej znajdziesz informacje potrzebne do zalogowania się na swarm master w Twoim klastrze.

- FQDN:
  - Uczestnicy nr. 01-24: sdclab\<NUMER>-master.eastus2.cloudapp.azure.com
  - Uczestnicy nr. 25-50: sdclab\<NUMER>-master.eastus.cloudapp.azure.com
- Klucz prywatny: swarm_master
- Login: sdcuser


## Sprawdź czy klaster jest uruchomiony i wszystkie nody są dostępne <a id="weryfikacja-klaster"/>
Wyświetl informacje o wszystkich nodach w Twoim klastrze; wykonaj komendę.

```
docker node list
```

## Uruchom usługę Wordpress w klastrze <a id="usluga-uruchomienie"/>

1. Na hoście swarm master załóż katalog na projekt (nazwa może być dowolna) i skopiuj do niego plik [docker-compose.yml](https://github.com/linuxpolska/docker-swarm-demo/blob/master/docker-compose.yml)
2. W katalogu projektu utwórz dwa pliki:
   - db_passswd.txt - plik z hasłem do konta root do bazy danych
   - wordrpes.txt - plik z hasłem do konta wordpress do bazy danych
4. Uruchom usługę w klastrze wydając komendę
    ```
    docker stack deploy --compose-file docker-compose.yml wordpress
    ```
## Sprawdź czy usługa została uruchomiona na klastrze

## Sprawdź czy serwis wordpress jest dostępny w Internecie

## Wyskaluj usługę wordpress

## Usuń usługę wordpress


