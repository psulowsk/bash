## Bash komendy

### Ogolne
*  Sciezka do interpretera, ktory ma byc uzyty do wykonania kodu
```bash
#![sciezka interpretera]
```
*  Komentarz
```bash
#[tresc komentarza]
```
*  Wyswietlanie informacji o typie komendy
```bash
type [nazwa komendy]
```

### Directory
*  Wyswietlanie zawartosci aktualnego directory
```bash
ls
```
*  Zmiana aktualnego directory
```bash
cd [docelowe directory]
```
*  Printowanie aktualnego directory
```bash
pwd
```
*  Tworzenie nowego directory
```bash
mkdir [nowe directory]
```

### Files
* Tworzenie pustego pliku
```bash
touch [nazwa nowego pliku]
```
* Wyswietlanie zawartosci pliku
```bash
cat [nazwa pliku]
```
* Wyswietlanie informacji o pliku i jego statusu
```bash
stat [nazwa pliku]
```
* Przenoszenie pliku do innego directory
```bash
mv [nazwa pliku] [docelowe directory]
```
* Uruchomienie edytora nano
```bash
nano [nazwa pliku]
```
* Zmiana uprawnien do pliku
```bash
chmod [mode] [nazwa pliku]
Modes:
u+x - aktualny uzytkownik moze uruchmiac skrypt (?)
a+x - wszyscy uzytkownicy moga uruchamiac skrypt
```

### Text
* Printowanie teksty
```bash
echo [tekst]
```

## Variables
* Wczytywanie inputu z wiersza polecen 
```bash
read [nazwa zmiennej] >> wczytuje input do wskazanej zmiennej
read >> wczytuje input do zmiennej $REPLY

Opcje:
    -s - wczytuje input, ale go nie printuje (bez echo)
    -n1 - wczytuje input, ktory sklada sie z jednego znaku
```
* Wczytywanie inputu z wiersza polecen do zmiennej $REPLY
```bash
read
```
* Tworzenie zmiennej
```bash
[nazwa zmiennej]=[wartosc]
    UWAGA! przed i za znakiem rownosci nie moze byc spacji    
```
* Tworzenie zmiennej skladajacej sie z kilku zmiennych
```bash
[zmienna]="[zmienna_1], [zmienna_2]"
```
* Odwolanie sie do zmiennej
```bash
$[nazwa zmiennej] 
```
* Odwolanie sie do argumentow komendy
```bash
$* >> odwolanie sie do wszystkich argumentow jako stringu
$@ >> odwolanie sie do wszystkich argumentow jako array
$[indeks zmiennej] >> odwolanie sie do konkretnego argumentu (gdzie $0 to komenda, $1, $2... to kolejne argumenty)
```
* Liczba argumentow w komendzie
```bash
$#
```
* Lista zmiennych lokalnych
```bash
set
```
* Lista zmiennych srodowiskowych
```bash
env
```
### Zmienne srodowiskowe
```bash
$USER >> nazwa uzytkownika
```

### Zmienne srodowiskowe
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```
* 
```bash

```


