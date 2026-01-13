# Prezerntacja---Atak-brute-force
Rezpozytorium stworzone na potrzeby zajęć BAIiM

## Zadania
### ZAD 1 Audyt Osobisty i OSINT

1.	Narzędzie: Odwiedź stronę haveibeenpwned.com (HIBP).
2.	Działanie: Wpisz swój stary adres e-mail (np. z czasów szkolnych).
3.	Analiza: Sprawdź, w jakich wyciekach figuruje (np. "Collection #1", "Morele", "LinkedIn").
4.	Refleksja: Zobacz, jakie dane wyciekły (Hasła? Daty urodzenia?). Zastanów się, czy używałeś tego samego hasła w innych miejscach.

### ZAD 2: Pomysł na biznes

Cel: Oblicz, ile lat zajęłoby superkomputerowi Athena (AGH) włamanie się do dowolnego z istniejących portfeli z 12-wyrazową frazą seed.
Dane do obliczeń:
 - Wszystkie kombinacje (12 słów): ok. $3,4 \times 10^{38}$ (dla standardu BIP-39 który zakłada 2048 słów)
 - Liczba aktywnych portfeli do trafienia: $100\ 000\ 000$ ($10^8$)
 - Moc obliczeniowa Atheny: $100$ miliardów prób/sekundę ($10^{11}$)
 - Rok: ok. $31,5$ mln sekund
Pytanie: Ile lat trwałoby sprawdzanie fraz, aż statystycznie trafimy na jeden z aktywnych portfeli?
