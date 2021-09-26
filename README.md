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
* Tworzenie pliku z komend wpisanych w powloce
```bash
cat > [nazwa pliku] <<END
[tresc komendy]
END
```
* Porownanie 2 posortowanych plikow i zwrocenie jako output wyrazow wg wybranych opcji
```bash
comm [opcje] <(sort[nazwa_pliku_1]) <(sort [nazwa_pliku_2])

Opcje:
    -1 - pomin wiersze unikalne dla pliku_1
    -2 - pomin wiersze unikalne dla pliku_2
    -3 - pomin wiersze wystepujace w obu plikach
```
* Porownanie 2 posortowanych plikow i zwrocenie jako output UNIKALNYCH wyrazow wg wybranych opcji
```bash
comm [opcje] <(sort[nazwa_pliku_1] | uniq) <(sort [nazwa_pliku_2] | uniq)

Opcje: 
    jw.
```
* Wyswietlanie informacji o pliku
```bash
stat [nazwa pliku] -c %F >> wyswietlanie typu pliku
stat [nazwa pliku] -c %n >> wyswietlanie nazwy pliku
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
* Zastapywanie znakow w stringu
```bash
[string]/[znak do zastapienia]/[znak zastepujacy] >> zastapienie w stringu PIERWSZEGO wystapienia okreslonego znaku
[string]//[znak do zastapienia]/[znak zastepujacy] >> zastapienie w stringu WSZYSTKICH wystapien okreslonego znaku\
```
* Przeszukiwanie wzorca w pliku
```bash
grep [opcje] [szukany wzor] [przeszukiwany plik]
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
* Przypisywanie do zmiennej wyniku dzialan arytmetycznych
```bash
let [zmienna]=[dzialanie arytmetyczne]

lub

[zmienna]=$(([dzialanie arytmetyczne]))
```
* Wykonywanie dzialania arytmetycznego i zwracanie wyniku w powloce
```bash
expr [dzialanie arytmetyczne]

UWAGA! miedzy liczbami a operatorem musi byc spacja
```
* Przesuniecie pozycyjnych argumentow o n-pozycji (defaultowo n=1)
```bash
shift [liczba przesuniec]

Przyklad:
komenda shift 2 powoduje ze podajac $1 odwolujemy sie w rzeczywistosci do $3
```
* Ustawianie domyslnej wartosci dla zmiennej
```bash
[zmienna]:-[domyslna wartosc] >> ustawianie domyslnej wartosci dla zmiennej, ktora nie zostala zadeklarowana lub ma wartosc null
[zmienna]:-[domyslna wartosc] >> ustawianie domyslanej wartosci dla zmiennej, ktora nie zostala zadeklarowana (jesli zadeklarowana to zwroci null)
```

### Environment variables
```bash
$USER >> nazwa uzytkownika
```

### Options
* Wyswietlanie wszystkich opcji w powloce
```bash
shopt
```
* Wlaczenie okreslonej opcji
```bash
shopt -s [nazwa opcji]

lub

set -o [nazwa opcji]
```
* Wylaczenie okreslonej opcji
```bash
shopt -u [nazwa opcji]

lub

set +o [nazwa opcji]
```
* Wybrane opcje
```bash
set -o noclobber >> wylaczenie opcji nadpisywania plikow
set +o noclobber >> wlaczenie opcji nadpisywania plikow
set -f >> wylaczenie file 
set +f >> wlaczenie file globbing
set -x >> wlaczenie opcji debugowania
set +x >> wylaczenie opcji debugowania
set -o xtrace >> wlaczenie opcji debugowania
set +o xtrace >> wylaczenie opcji debugowania
shopt -s autocd >> włączenie opcji autocd
shopt +s autocd >> wyłączenie opcji autocd
```
* Wprowadzenie wybranych opcji do komendy (polecenie do przetwarzania argumentow wiersza polecen)
```bash
getopts ':[nazwa_opcji_1]' >> wprowadzenie do komendy opcja_1 i ustawienia, że getopts nie zwróci żadnej diagnostic message w przypadku brakującej lub niepoprawnej opcji
getopts '[nazwa_opcji_1]:' >> wprowadzenie do komendy opcja_1, ktora wymaga argumentu (do którego możemy się odwołać jako do $OPTARG)
getopts '[nazwa_opcji_1]' >> wprowadzenie do komendy opcja_1, ktora nie wymaga argumentu
getopts ':[nazwa_opcji_1]:[nazwa_opcji_2]:' >> wprowadzenie do komendy opcja_1 i opcja_2, ktore wymagaja argumentow i ustawienia, że getopts nie zwróci żadnej diagnostic message w przypadku brakującej lub niepoprawnej opcji
```
* Znak zakonczenia opcji (zapobiega sytuacji w ktorej opcja zostanie potraktowana jako zmienna)
```bash
--
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

### Condition
* Postac warunku
```bash
[[ [warunek] ]] 

UWAGA! obowiazkowo spacja miedzy warunkiem a nawiasami
```
* Operator logiczny AND
```bash
[[ warunek_1 && warunek_2 ]]
```
* Operator logiczny OR
```bash
[[ warunek_1 || warunek_2]]
```
UWAGA1! Przy porownywaniu mozna uzywac wymienie = i ==
UWAGA2! Przy porownywaniu znaki = i == musza byc z lewej i prawej strony oddzielone spacja
* Wybrane warunki dot. tekstu
```bash
[[ $[tekst] ]] >> sprawdza czy string jest pusty 
[[ $[teskt] = '[wartosc]' ]] >> sprawdza czy string jest rowny wybranej wartosci
[[ $[teskt] != '[wartosc]' ]] >> sprawdza czy string nie jest rowny wybranej wartosci
[[ $[teskt] = '*[wartosc]' ]] >> sprawdza czy string konczy sie na okreslona wartosc
[[ $[teskt] =~ [wartosc]$ ]] >> sprawdza czy string konczy sie na okreslona wartosc
```
* Wybrane warunki dot. porownywania wartosci
```bash
[[ $[nazwa zmiennej] -gt [wartosc] ]] >> sprawdza czy zmienna > wartosc
[[ $[nazwa zmiennej] -lt [wartosc] ]] >> sprawdza czy zmienna < wartosc
[[ $[nazwa zmiennej] -ge [wartosc] ]] >> sprawdza czy zmienna >= wartosc
[[ $[nazwa zmiennej] -le [wartosc] ]] >> sprawdza czy zmienna <= wartosc

lub analogicznie

(( [nazwa zmiennej > [wartosc] ))
(( [nazwa zmiennej < [wartosc] ))
(( [nazwa zmiennej >= [wartosc] ))
(( [nazwa zmiennej <= [wartosc] ))

UWAGA! korzystajac z okraglych nawiasow (), przy zmiennej nie ma koniecznosci podawac $
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
* Wykonanie polecenia, gdy spelniony warunek
```bash
[[ [warunek] ]] && [polecenie]
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
* Wybrane warunki dot. plikow i innych obiektow
```bash
[[ -f $[nazwa pliku ]] >> sprawdza czy istnieje regularny plik
[[ -e $[nazwa pliku ]] >> sprawdza czy istnieje plik dowolnego typu
[[ ! -e $[nazwa pliku ]] >> sprawdza czy nie istnieje plik dowolnego typu
[[ -d $[nazwa directory ]] >> sprawdza czy istnieje directory
[[ -L $[nazwa symbolic link ]] >> sprawdza czy istnieje symbolic link
[[ -r $[nazwa pliku ]] >> sprawdza czy plik ma read-only permission
[[ -w $[nazwa pliku ]] >> sprawdza czy plik ma write permission
[[ -x $[nazwa pliku ]] >> sprawdza czy plik ma execute permission
[[ -k $[nazwa pliku ]] >> sprawdza czy istnieje sticky bit
[[ -s $[nazwa pliku ]] >> sprawdza czy istnieje suid bit
[[ ! $1 ]] >> sprawdza czy uzytkownik wpisal pierwszy argument
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

### Redirection
* Przekazanie outputu komendy (STDOUT) do pliku
```bash
[komenda] > [nazwa pliku]
```
* Przekazanie erroru z komendy (STDERR) do pliku
```bash
[komenda] 2> [nazwa pliku]
```
* Przekazanie outputu (STDOUT) i erroru z komendy (STDERR) do pliku
```bash
[komenda] &> [nazwa pliku]
```
* Przekazanie outputu kilku komend (STDOUT) do pliku
```bash
([komenda_1]; [komenda_2]) > [nazwa pliku]
```
* Przekierowanie outputu komend z powloki do okreslonego pliku
```bash
exec > [nazwa pliku]
```
* Stworzenie nowego descriptora, ktory jest duplikatem istniejacego descriptora
```bash
exec [nowy descriptor] > $[numer istniejacego descriptora]
```
* Usuniecie descriptora
```bash
exec [istniejacy descriptor] > &--
```

### Job management
* Opoznienie wykonania komendy  okreslony czas (defaultowo w sekundach)
```bash
sleep [czas]
sleep [czas]& >> opoznienie i uruchomienie komendy w tle
```
* Wykonywanie procesu nawet po wylogowaniu lub rozlaczeniu z aktualna powloka
```bash
nohup
```
* Zaplanowanie wykonania skryptu o konkretnej porze (i przydzieleniu mu job id)
```bash
at [czas wykonania skryptu] [skrypt do wykonania]

UWAGA! at pozwala zaplanowac JEDNORAZOWE uruchomienie skryptu
```
* Usuniecie joba
```bash
atrm [job id]

lub

rm [nazwa joba]
```
* Wyswietlenie szczegolow dot. joba 
```bash
at -c [job id]
```
* Wyswietlenie listy wszystkich jobow
```bash
atq

lub 

crontab -l
```
* Dodanie nowego joba - uruchomienie ponizszej komendy otwiera edytor, w ktorym umiescic komende i czas CYKLICZNEGO wykonywania
```bash
crontab -e
```
* Dodanie nowego joba (drugi sposob bez otwierania edytora)
```bash
crontab -l > [nazwa nowego joba]
[czas wykonania joba] [komenda joba] > [nazwa nowego joba]
crontab [nazwa nowego joba]

Przyklad:
crontab -l > mycron
echo "00 09 * * 1-5 echo hello" >> mycron
crontab mycron
```
* Format czasu wykonania joba
```bash
* * * * *
- - - - -
| | | | |--- Day of week (0-7) (Sunday=0 or 7)
| | | | ---- Month (1-12)
| | |------- Day of month (1-31)
| |--------- Hour (0-23)
| ---------- Minute (0-59)
```
* Lista aktualnie uruchomionych procesow
```bash
ps
```

### Others
* Sprawdzanie czy sa bledy w skrypcie
```bash
shellcheck [nazwa skryptu]
```
* Uruchomianie restricted bash
```bash
rbash 
```
* Tworzenie aliasu
```bash
alias [komenda]="[alias dla komendy]"
```
* Usuwanie aliasu
```bash
unalias [komenda]
```





