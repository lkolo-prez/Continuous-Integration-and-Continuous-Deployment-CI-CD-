# Jenkins CI/CD

Jenkins jest otwartoźródłowym narzędziem do automatyzacji, które oferuje platformę do modelowania, uruchamiania, testowania i wdrażania kodu źródłowego. W tym pliku README znajdują się podstawowe informacje na temat korzystania z Jenkinsa.

## Instalacja

Do instalacji Jenkinsa na serwerze Linux, użyj następujących poleceń:

```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```

## Uruchomienie

Jenkinsa można uruchomić za pomocą następującego polecenia:

```bash
sudo systemctl start jenkins
```

Jenkins jest teraz dostępny na porcie 8080. Możesz go otworzyć w przeglądarce internetowej, wpisując adres `http://localhost:8080`.

## Konfiguracja

Po pierwszym uruchomieniu Jenkinsa będziesz musiał wprowadzić kod odblokowujący. Ten kod można znaleźć w pliku logów:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Następnie, postępuj zgodnie z instrukcjami kreatora konfiguracji, który pojawi się przy pierwszym uruchomieniu.

## Tworzenie pierwszego projektu (Job)

1. Po zalogowaniu do panelu Jenkinsa, kliknij "New Item" w menu.
2. Wpisz nazwę projektu, wybierz "Freestyle project", a następnie kliknij "OK".
3. W konfiguracji projektu, można określić źródło kodu, budowanie projektu, testy itp.
4. Kliknij "Save" po zakończeniu konfiguracji.

## Uruchamianie projektu

Projekt można uruchomić ręcznie, klikając "Build Now" w menu projektu. Jenkins oferuje również wiele opcji automatycznego uruchamiania projektów, takich jak uruchamianie po każdej zmianie w kodzie źródłowym.

## Dokumentacja

Więcej informacji na temat Jenkinsa można znaleźć na oficjalnej stronie dokumentacji: [https://www.jenkins.io/doc/](https://www.jenkins.io/doc/)

## Wsparcie

Jeśli napotkasz problemy podczas korzystania z Jenkinsa, możesz znaleźć pomoc na oficjalnym forum: [https://community.jenkins.io/](https://community.jenkins.io/)

---
