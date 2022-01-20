# SSRF LAB
## Przygotowanie środowiska (Zadania 1 - 3)

### Opcja 1 - Docker
1. Zainstaluj docker'a.
2. Pobierz plik [ssrf_lab.tar.gz](https://drive.google.com/drive/folders/1HPTJYjlRWKUwC4ak-E6y4DsqCtxsFD1j?usp=sharing)
3. Otwórz terminal
4. docker load < scieżka/do/pliku/ssrf_lab.tar.gz
5. docker run -i --rm -p 3000:80 ssrf-lab
6. Otwórz w przeglądarce http://localhost:3000

### Opcja 2 - Maszyna wirtualna
1. Pobierz plik [ssrf-lab-2.ova](https://drive.google.com/drive/folders/1HPTJYjlRWKUwC4ak-E6y4DsqCtxsFD1j?usp=sharing)
2. Zaimportuj plik za pomocą VirtualBox i uruchom maszyne wirtualną
3. Otwórz terminal i wpisz komende: start-lab (hasło do root'a: student)
4. Zostanie uruchomiona aplikacja pod adresem http://localhost:3000 i serwer XAMPP pod adresem http://localhost

<br>

## Zadanie 0
Pod podanym [linkiem](https://application.security/free-application-security-training/server-side-request-forgery-in-capital-one) znajduje się interaktywny tutorial przedstawiający jak wyglądał hack na Capital One, wspomniany w prezentacji. Jako rozwiązanie wystarczy przesłać screenshot z ostatniego panelu tutorialu.

<br>

## Zadanie 1
Zadanie polega na uzyskaniu zasobu, który jest dostępny tylko z poziomu serwera. Jako raport wyślij zrzut ekranu i zmodyfikowane zapytanie, jakie zostało użyte. 
<details>
<summary>Hint 1</summary>
  <br>
 <ul><li>Zaboserwuj odpowiedź aplikacji ze statusem 403: F12 -> Network -> F5</li></ul>
</details>
<details>
<summary>Hint 2</summary>
  <br>
 <ul><li>Zauważ, że aplikacja ładuje zasoby przez przekazanie ścieżki do zmiennej GET</li></ul>
</details>
<br>

## Zadanie 2
Należy uzyskać dostęp do zdjęcia o nazwie image.jpg znajdującego się w folderze /local/secret, który chroniony jest blacklistą.
Można to zrobić na różne sposoby:
- Sposób 1: Blacklistę można ominąć tworząc własną stronę, która przekierowuje na adres localhost z odpowiednią ściężką do zasobu. W tym celu:
	- uruchom xampp'a, następnie edytuj plik index.php
	- skorzystaj z funkcji [header](https://www.php.net/manual/en/function.header.php)
- Sposób 2: można próbować wpisywać różne payload'y i liczyć na to, że nie są na blackliście :D

<br>

<details>
<summary>Hint do sposobu 1</summary>
  <br>
 <ul><li>Wpisz w odpowiednim miejscu adres serwera XAMPP (jako adres interfejsu sieciowego)</li></ul>
</details>

<br>

Jako raport wyślij zrzut ekranu z uzyskanym zdjęciem i użytem adresem URL.

<br>

## Zadanie 3
Trzeba dostać się do pliku /secret/file. Aplikacja blokuje wszystkie zasoby pod adresem /secret za pomocą 2-elementowej whitelisty. Dla uproszczenia została stworzona [lista](list.txt), na której znajdują się dozwolone nazwy hostów. Sugerujemy skorzystać z narzędzia Intruder z programu Burp Suite.

Jako raport wyślij zrzut ekranu i podaj 2 znalezione adresy hostów, które znajdują sie na whiteliście.
