#Laboratorium 1
zd.1 Używając linii poleceń stwórz strukturę katalogów:

temp |-- dom |-- nauka | |-- c | |-- logo | -- pascal -- praca |-- dokumenty -- zlecenia |-- niezrealizowane -- zrealizowane
```sh

mkdir -p temp/dom
mkdir -p temp/nauka/{c,logo,pascal}
mkdir -p temp/praca/{dokumenty,zlecenia}
mkdir -p temp/praca/zlecenia/{niezrealizowane,zrealizowane}
cd temp | tree
```
zd.2 Przejdź do katalogu dom i utwórz katalog wazne-sprawy.
```sh

cd dom
mkdir wazne-sprawy
```
zd.3 Wejdź do katalogu wazne-sprawy i utwórz tam pusty plik rachunki.txt.
```sh

cd wazne-sprawy
touch rachunki.txt
```
zd.4 Będąc w katalogu wazne-sprawy skopiuj plik rachunki.txt do katalogu zrealizowane.
```sh
cp rachunki.txt ../../praca/zlecenia/zrealizowane/rachunki.txt
```
zd.5 Przejdź do katalogu zrealizowane i zmień nazwę pliku rachunki.txt na wykonano.txt.
```sh
 
cd ../..
cd praca/zlecenia/zrealizowane
mv rachunki.txt wykonano.txt
```
zd.6 Utwórz plik wykonano.txt wielkości 11 bajtów, następnie podziel go pliki wielkości 5 bajtów. 
W ten sposób otrzymasz 3 pliki. (split)
```sh

cat > wykonano.txt 
12345678901 (nastepnie Ctrl+D)
split -b 5 wykonano.txt
```
zd.7 Będąc w katalogu logo skopiuj powyżej otrzymane 3 pliki do katalogu dokumenty.
```sh
cp ../../praca/zlecenia/zrealizowane/x* ../../praca/dokumenty
```
zd.8 Będąc w katalogu dokumenty połącz skopiowane 3 pliki w plik odtworzono.txt, 
tak aby otrzymać plik o zawartości identycznej z wykonano.txt. 
Następnie plik odtworzono.txt skopiuj do katalogu wazne-sprawy.
```sh

cat xaa xab xac > odtworzono.txt
cp odtworzono.txt ../../dom/wazne-sprawy/odtworzono.txt
```
zd.9 Będąc w katalogu wazne-sprawy sprawdź, czy są jakieś różnice w zawartości plików wykonano.txt i odtworzono.txt.
```sh
diff -a ../../praca/zlecenia/zrealizowane/wykonano.txt odtworzono.txt
```
zd.10 Wyświetl kalendarz na październik 2009 r. (cal)
```sh
cal 10 2009
```
Wyświetl kalendarz na wrzesień, październik i listopad 2009 r. z miesiącami obok siebie (cal):
```sh
cal -3 2009
```
zd.11 Jaki był dzień tygodnia 25 maja 1975 r. (cal i date)
```sh
date -d 1975-05-25 +%A
```
#Laboratorium 2
Zad.1 Wyświetl na ekran 2 pierwsze wiersze pliku program.c. (head)
```sh
head -n 2 program.c
```
zd.2 Wyświetl na ekran 4 ostatnie wiersze pliku program.c. (head,tail)
```sh
tail -n 4 program.c
```
Zad.3 W pliku program.c znajdź wszystkie wiersze z wystąpieniem słowa „main”. (grep)
```sh
grep "main" program.c
```
zd.4 Plikowi program.c nadaj następujące uprawnienia: właściciel – czytanie, pisanie, 
grupa – czytanie, pozostali użytkownicy: brak uprawnień. (chmod)
```sh
chmod 650 program.c
```
zd.5 Będąc w katalogu temp przenieś katalog wazne-sprawy do katalogu praca.
```sh
mv dom/wazne-sprawy praca/wazne-sprawy
```
zd.6 Zarchiwizuj cały katalog temp. (zip i tar)
```sh
tar -cvf temp.tar temp
gzip temp.tar
```
zd.7 Usuń katalog temp.
```sh
rm -rf temp
```
zd.8 Odtwórz z archiwum katalog temp. (unzip i tar)
```sh
tar -zxf temp.tar.gz
```
zd.9 Posprzątaj na swoim koncie.
```sh
cd ~/tmp
rm -rf *
```
#Laboratorium 3

Zad.1 Wyświetl plik /etc/passwd z podziałem na strony przyjmując, że strona na 5 linii tekstu.
```sh
more -5 /etc/passwd
```
zd.2 Korzystając z polecenia cat utwórz plik tekst3.txt, który będzie składał się z zawartości
pliku tekst1.txt, ciągu znaków podanego ze standardowego wejścia (klawiatury) i pliku tekst2.txt.
```sh 
cat tekst1.txt - tekst2.txt > tekst3.txt
```
lub
```sh
cat tekst1.txt > tekst3.txt
cat >> tekst3.txt
cat tekst2.txt >> tekst3.txt
```
Zad.3 Wyświetl po 5 pierwszych linii wszystkich plików w swoim katalogu domowym w taki sposób,
aby nie były wyświetlane ich nazwy.
```sh
head home/* -n 5 -q
```
lub
```sh
head -qn 5 *
```
zd.4 Wyświetl linie o numerach 3, 4 i 5 z pliku /etc/passwd.
```sh
head -n 5 /etc/passwd | tail -n 3
```
zd.5 Wyświetl linie o numerach 7, 6 i 5 od końca pliku /etc/passwd.
```sh
tail -n 7 /etc/passwd | head -n 3 
```
zdd.6 Wyświetl zawartość pliku /etc/passwd w jednej linii.
```sh
cat /etc/passwd |tr "n" " "
```
zd.7 Za pomocą filtru tr wykonaj modyfikację pliku plik.txt, polegającą na umieszczeniu każdego słowa w osobnej linii.
```sh
cat plik.txt | tr " \t" "\n"
```
zd.8 Zlicz wszystkie pliki znajdujące się w katalogu /etc i jego podkatalogach.
```sh
find /etc -type f 2> dev/null/ wc -l
```
lub
```sh
find /etc -type f 2> errors | wc -l
```
zd.9 Napisać polecenie zliczające ilość znaków z pierwszych trzech linii pliku /etc/passwd.
```sh
find /etc/ | head -3 | wc | tr '''\n' | tail -1
```
lub
```sh
find /etc/ | head -3 | wc -c
```
lub
```sh
cat /etc/passwd/ | head -n 3 | wc -m
```
lub
```sh
head /etc/passwd -n 3 | wc -c
```
#Laboratorium 4

zd.1 Wyświetl listę plików z aktualnego katalogu, zamieniając wszystkie małe litery na duże.
```sh
ls | tr [:lower:] [:upper:] (nie obsługuje znaków narodowych)
```
lub
```sh
ls | tr a-z A-Z
```
dla polskich liter:
```sh
ls | tr [:lower:]ąęćłśżź [:upper:]ĄĘŁŚŻŹ
```
zd.2 Wyświetl listę praw dostępu do plików w aktualnym katalogu, ich rozmiar i nazwę.
```sh
ls -l | awk '{print $1,$5,$9}'
```
lub
```sh
find . -type f -exec ls -l '{}' ';' | cut -d ' ' -f1,5,9
```
lub
```sh
ls --format=long --human-readable
```
zd.3 Wyświetl listę plików w aktualnym katalogu, posortowaną według rozmiaru pliku.
```sh
ls -l | sort -k5,5
```
lub
```sh
ls -lrS
```
lub
```sh
find . -maxdepth 1 -not - type d -exec ls -l '{}' ';' | sort -n -t ' ' -k6,6
```
lub
```sh
ls --sort=size -1
```
zd.4 Wyświetl zawartość pliku /etc/passwd posortowaną według numerów UID w kolejności od największego do najmniejszego.
```sh
cat /etc/passwd | sort -n -t ':' -k3,3
```
lub
```sh
sort -t : -n -k3 -r /etc/passwd
```
lub
```sh
cat /etc/passwd | sort -r -t: -g -k 3
```
lub
```sh
sort -t : -k3 -nr
```
zd.5 Wyświetl zawartość pliku /etc/passwd posortowaną najpierw według numerów GID w kolejności od największego do najmniejszego, a następnie UID.
```sh
sort -t : -k4 -r /etc/passwd | sort -t : -k3 
```
lub
```sh
cat /etc/passwd | sort --field-separator=":" 
```
zd.6 Podaj liczbę plików każdego użytkownika.
```sh
find $HOME -not -type d| wc -l
```
zd.7 Sporządź statystykę praw dostępu (dla każdego z praw dostępu podaj ile razy zostało ono przydzielone).
```sh
find -printf "%m\n" | sort | uniq -c
```
Efekt wykonania poniższych poleceń?
1) ls -l > lsout.txt
```sh
Utwotrzenie pliku lsout.txt i wypelnienie jej lista plikow w akutalnym katalogu
```
2) ls -la >> lsout.txt
```sh
Dopisuje do pliku lsout.txt liste uruchomionych procesów
```
3) ps >> psout.txt
```sh
Dopisuje ilosc wolnej pamięci
```
#Laboratorium 5
zd.1 Znajdź w swoim katalogu domowym (bez podkatalogów) wszystkie pliki, które zostały zmodyfikowane w ciągu ostatnich dziesięciu dni i wyświetl ich nazwy.
```sh
find ~/ -maxdepth 1 -mtime -10
```
zd.2 Znajdź wszystkie pliki zwykłe w systemie, które mają w nazwie ciąg znaków „conf” i wyświetl ich nazwy na ekranie.
```sh
find  / -name \*config\* -type f 2> /dev/null
```
zd.3 Znajdź w swoim katalogu domowym wszystkie pliki, które nie były używane w ciągu ostatnich 20 dni.
```sh
find ~/ -atime 20
```
zd.4 Znajdź w katalogu /etc wszystkie niepuste podkatalogi i pliki o nazwach zaczynających się na literę „a”.
```sh
find /etc \( -type f -and -name a* \) -or \( -type d -and ! -empty \) 2> /dev/null
```
Zadania różne

Zad.5 Z bieżącego katalogu usuń pliki, których nazwa zaczyna się na literę „x” i zawiera dokładnie trzy znaki.
```sh
rm x??
```
Zad.6 Skonstruuj polecenie tworzące katalog, którego nazwą będzie aktualna (w momencie wywołania) systemowa data w formacie rrrr-mm-dd.
```sh
mkdir date +%Y-%m-%d
```
#Laboratorium 6

Zad.1 W pliku plik.txt znajdź wiersze zawierające co najmniej jeden znak.
```sh
grep . {1,} plik.txt
```
Zad.2 Znajdź w plikach pl* wiersze rozpoczynające się od cyfry.
```sh
grep ^[0-9] pl*
```
Zad.3 Znajdź pliki, zawierające wiersz w którym na 9 pozycji występuje litera r.
```sh
ls -1 | grep -E '^.{8}r.*'
```
Zad.4 Policz, ilu użytkowników systemu używa powłoki bash (zgodnie z zapisami w pliku /etc/passwd).
```sh
grep -c bash /etc/passwd
```
Zad.5 Znajdź wiersze zawierające liczby rzymskie w pliku plik.txt.
```sh
egrep "(X|D|C|M|V|L|I){1,}" plik.txt
```