## Bash commands

### General
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
* Printowanie tekstu
```bash
echo [tekst]
```
* Printowanie tekstu ze zmiennymi 
```bash
printf "[tekst]%s[dalszy tekst]%s[dalszy tekst...]\n" $[zmienna_1] $[zmienna_2]

Komentarz
    - za %s podstawiane sa kolejne zmienne wskazane na koncu stringa
    - \n powoduje przejscie do kolejnej linii
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

UWAGA! 
    przed i za znakiem rownosci nie moze byc spacji    
```
* Tworzenie zmiennej skladajacej sie z kilku zmiennych
```bash
[zmienna]="[zmienna_1], [zmienna_2]"
```
* Odwolanie sie do zmiennej
```bash
$[nazwa zmiennej] 
${[nazwa zmiennej]} >> zmienna powinno brac sie w {} nawiasy, aby poinformowac gdzie konczy sie nazwa zmiennej
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
* Lista wszystkich zmiennych 
```bash
declare

Opcje:
    -p - printuje liste zmiennych z ich opcjami
    -f - printuje liste zmiennych z ich detalami
    -F - printuje same nazwy zmiennych

```
* Deklarowanie zmiennych
```bash
declare [nazwa zmiennej]

Opcje:
    -x - deklaruje zmienna jaka srodowiskowa (dostepna poza aktualna powloka)
    +x - usuwa zmienna spoza scope'u srodowiskowego
    -u - wartosci zmiennych z wielkich liter
    -l - wartosci zmiennych z malych liter
    -i - zmienna jako integer
    -r - zmienna read-only (brak mozliwosci zmiany przypisanej wartosci)
```
* Eksportowanie zmiennej jako scope'u srodowiskowego
```bash
export [nazwa zmiennej]
```
* Usuwanie zmiennej ze scope'u srodowiskowego
```bash
unset [nazwa zmiennej]
```

### Array
* Deklarowanie array
```bash
declare -a [nazwa array]
declare -a [nazwa array]=([0]=[wartosc_1] [1]=[wartosc_2] ...) >> deklarowanie array i jego wartosci
[nazwa array]=([wartosc_1] [wartosc_2] [wartosc_3] [wartosc_4]) >> drugi sposob na deklarowanie array
```
* Wszystkie elementy z array
```bash
[nazwa array][*]
```
* Wszystkie indeksy z array
```bash
![nazwa array][*]
```
* Liczba wyrazow w array
```bash
#[nazwa array][*]
```
* n-ty wyraz z array
```bash
[nazwa array][n]
```

### Environment variables
```bash
$USER >> nazwa uzytkownika
```

### Condtition
* Postac warunku
```bash
[[ [warunek] ]] 

UWAGA! obowiazkowo spacja miedzy warunkiem a nawiasami
```
* Wybrane warunki
```bash
UWAGA1! Przy porownywaniu mozna uzywac wymienie = i ==
UWAGA2! Przy porownywaniu znaki = i == musza byc z lewej i prawej strony oddzielone spacja

[[ $[tekst] ]] >> sprawdza czy string jest pusty 
[[ $[teskt] = '[wartosc]' ]] >> sprawdza czy string jest rowny wybranej wartosci
[[ $[teskt] != '[wartosc]' ]] >> sprawdza czy string nie jest rowny wybranej wartosci
[[ $[teskt] = '*[wartosc]' ]] >> sprawdza czy string konczy sie na okreslona wartosc
[[ $[teskt] =~ [wartosc]$ ]] >> sprawdza czy string konczy sie na okreslona wartosc
[[ $[] ]] >> sprawdza czy 
[[ $[] ]] >> sprawdza czy 
[[ $[] ]] >> sprawdza czy 
[[ $[] ]] >> sprawdza czy 
[[ $[] ]] >> sprawdza czy 

```

### Conditional statement
* Postac conditional statement
```bash
if [warunek]; then [polecenie]; elif [polecenie]; else [polecenie]; fi

lub

if [warunek]
then
    [polecenie]
elif
    [polecenie]
else
    [polecenie]
fi
```

### Case statement
* Postac case statement
```bash
case $[zmienna] in
    [wartosc_1])
        [polecenie]
    [wartosc_2])
        [polecenie]
    [wartosc_3])
        [polecenie]
    [wartosc_4])
        [polecenie]
esac
```

### Function
* Postac funkcji
```bash
function [nazwa funkcji]{
    [polecenie]
}
```
* Deklarowanie funkcji 
```bash
declare [nazwa funkcji]

Opcje:
    -x - deklarowanie funkcji do scope'u srodowiskowego (dostepnej poza aktualna powloka)
```
* Usuwanie funkcji 
```bash
unset -f [nazwa funkcji]
```

### Loops
* Postac petli WHILE
```bash
while (( [warunek] ))
do
    [polecenie]
done
```
* Postac petli UNTIL
```bash
until (( [warunek] ))
do
    [polecenie]
done
```
* Postac petli FOR
```bash
for (([zmienna]=[wartosc poczatkowa]; [zmienna][< lub >][wartosc koncowa]; [zmienna][++ lub --]))
do 
    [polecenie]
done

Przyklad:
for ((i=0;i<5;i++))
do
    [polecenie]
done
```
* Postac petli FOR dzialac na array
```bash
for (([zmienna]=[wartosc poczatkowa];[zmienna][< lub >] ${#[nazwa array][*]; [zmienna][++ lub --]))
do 
    [polecenie]
done

Przyklad:
for ((i=0;i<${#array[*]};i++))
do
    [polecenie]
done
```
* Skrocona postac petli FOR dzialac na array
```bash
for [zmienna] in ${[nazwa array][*]}
do
    [polecenie]
done

Przyklad:
for i in ${array[*]}
do
    [polecenie]
done
```
* Postac petli FOREACH
```bash
for [zmienna] (${[nazwa array][*]})
    [polecenie]
end

Przyklad:
foreach i (${array[*]})
    [polecenie]
end

UWAGA! petla FOREACH dostepna tylko dla Z Shell
```
* Koniec aktualnej interacji petli i przejscie do kolejnej iteracji
```bash
continue
```
* Koniec petli
```bash
break
```

### Others
* Sprawdzanie czy sa bledy w skrypcie
```bash
shellcheck [nazwa skryptu]
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


