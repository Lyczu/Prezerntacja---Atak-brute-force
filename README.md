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
