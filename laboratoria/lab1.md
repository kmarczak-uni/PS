# Wprowadzenie

Python to język wysokiego poziomu, dynamicznie typowany i interpretowany (a nie kompilowany). W przeciwieństwie do C, Python nie wymaga deklarowania typów zmiennych i zarządzania pamięcią. Jego składnia jest bardziej czytelna i zwięzła.

# Uruchamianie Pythona

Kod w Pythonie można uruchamiać w interpreterze interaktywnym lub zapisywać w plikach .py i uruchamiać za pomocą python nazwa_pliku.py w konsoli.
  
Język C:  
```c
#include <stdio.h>

int main() {
  int array[3] = { 1, 2, 3 };
  for(int i = 0; i < 3; i++) {
    printf("%d\n", array[i]);
  }
  return 0;
}
```

Python:

```python
# komentarz: przykladowy program w jezyku Python
numbers = [1, 2, 3]
for i in numbers:
    print(i)
```

## Zadanie   
Porównaj powyzsze programy i wymień wszystkie różnice między językiem C i Python, które są widoczne w tym przykładzie. Uruchom przykładowy program zarówno w IDLE, jak i w terminalu.

# Definiowanie funkcji

W Pythonie funkcje definiuje się za pomocą słowa kluczowego `def`.
```python
def multiply(a, b):
    return a * b

result = multiply(3, 4)
print(f'{a} * {b} = {result}')
```  
Powyższy przykład używa tak zwanych `f-strings` do formatowania napisu. Więcej na ten temat: https://docs.python.org/3/tutorial/inputoutput.html

## Zadanie  
Napisz funkcję, która zapyta użytkownika o jego imię i wypisze komunikat z uzyciem tego imienia (np. "Witaj, Jan Kowalski!"). Potrzebną funkcję biblioteczną znajdziesz w [dokumentacji.](https://docs.python.org/3/library/functions.html#built-in-functions) Pamiętaj o użyciu `f-strings`.

# Zarządzanie modułami
  
Python posiada bogaty ekosystem modułów, które można importować i używać w swoich programach. Moduły pozwalają na organizację kodu oraz ponowne wykorzystanie gotowych funkcji i klas.
  
Mozna importować cały moduł, a pochodzące z niego elementy nalezy poprzedzać nazwą modułu:
```python
import math
print(math.sqrt(16))
```
lub tylko wybrane elementy (stałe, funkcje itd.).
```python
from math import sqrt
print(sqrt(16))
```
Można również nadawać importowanym modułom w swoim programie dowolny alias (uważając na kwestie przesłonięcia innej nazwy):
```python
import pandas as pd
import math as moj_ulubiony_przedmiot
```

### Instalacja nowych modułów spoza biblioteki standardowej opisana jest na końcu laboratorium.
  
## Zadanie  
Sprawdź działanie instrukcji `import this`.
  
# Typy zmiennych

Python jest językiem dynamicznie typowanym. To znaczy, ze typ zmiennej jest określany w trakcie przypisania wartości i może się zmienić w czasie działania programu.

```python
var = 'Ala ma kota'  # napis, czyli typ str (string)
print(f'Wartość zmiennej={var}, typ={type(var)}')
var = 12345  # typ int (liczba całkowita)
print(f'Wartość zmiennej={var}, typ={type(var)}')
var = 0.4533113  # typ float (liczba zmiennoprzecinkowa)
print(f'Wartość zmiennej={var}, typ={type(var)}')
```

Proste typy:
```python
str      # string - łańcuch znakowy
bool     # boolean - wartość logiczna prawda/fałsz
int      # integer - liczba całkowita
float    # floating point number - liczba zmiennoprzecinkowa
complex  # complex - liczb zespolona
```

Złożone typy (struktury danych):
```python
list      # lista - odpowiednik tablicy, kluczem jest indeks 
dict      # słownik, kluczem może być (prawie) dowolna wartość
set       # zbiór unikalnych wartości, kluczem jest indeks
tuple     # krotka - niemodyfikowalny odpowiednik listy
```

Przykłady użycia struktur danych:
  
```python
# lista
lista = [1, 2, 3, 'abc', True]  # uwaga - nie nazywac zmiennej "list" (dlaczego?)
print(lista[3])
lista[2] = 4
lista.append(6)
print(lista)
print(f'Dlugosc listy: {len(lista)}')

# słownik
slownik = {
  'k1': 'ala ma kota',
  'k2': 1337,
  'moja_lista': lista,
  1: 'one'
}

print(slownik[1])
slownik[1] = 'jeden'  # modyfikacja wartosci pod kluczem 1
slownik[2] = 'dwa'  # dodanie nowej pary klucz-wartosc
print(slownik)

# zbior
zbior = set([1, 2, 3, 1, 2, 3, 4])  # jeden argument: lista wartosci
print(zbior)
zbior.add(9)
print(zbior)
zbior = {1, 2, 3, 1, 2, 3, 4}  # alternatywna składnia tworzenia zbioru

krotka = (1, 4, 5, 3, 2, 1)
print(krotka)
print(krotka[1])
# krotka[1] = 0  wywoła błąd!
```

Iterowanie po strukturach danych  
  
W Pythonie nie musimy znać rozmiaru kolekcji (listy, zbioru itd.) aby móc ją przeiterować.  
Pętla `for` przechodzi po kazdym elemencie, az do końca kolekcji:  
```python
lista = ['q', 'w', 'e']
for element in lista:
    print(element, end=" ")
```
  
**Zadania**  
  
1. Stwórz listę zawierającą liczby całkowite od 1 do 10 000, używajac `range` [(dokumentacja)](https://docs.python.org/3/library/stdtypes.html#range). Następnie użyj pętli, aby każdą liczbę w liście zwiększyć o 1.  
2. Napisz funkcję, ktora zwróci listę krotek. Każda krotka to para liczb naturalnych dająca sumę `2*n`. Wartosc `n` jest parametrem funkcji. Np. lista dla n=50: `[(0, 100), (1, 99), (2, 98), ..., (99, 1), (100, 0)]`
3. Stwórz słownik przechowujący w kluczu imię i nazwisko osoby, a w wartości datę jej urodzin (wartości mają być zdefiniowane w programie, nie wpisane przez użytkownika). Do słownika zapisz 3 różne osoby. Do przechowania daty użyj typu `date` z modułu `datetime` ([dokumentacja](https://docs.python.org/3/library/datetime.html#examples-of-usage-date)).
4. Przetestuj, które z omówionych powyżej typów danych można użyc w roli klucza w słowniku. Następnie porównaj swoje obserwacje z informacjami w [tym artykule](https://wiki.python.org/moin/DictionaryKeys).
5. Poczytaj o [listach składanych](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions). Przepisz poniższe pętle tak, by używały składania list (tworzyły tę samą listę w jednej linii).
```python
values = []
for i in range(10):
    numbers.append(i**2)

values = []
for i in range(1, 6):
    for j in range(1, 4):
        values.append((i, j))
```

# przerwa :)

# Sterowanie przebiegiem programu

Instrukcja warunkowa `if`:
```python
wiek = 21
if wiek < 0:
    print("Wiek nie moze byc ujemny!")
elif x < 18:
    print("Jestes niepelnoletni.")
else:
    print("Jestes pelnoletni.")
```
  
Pętla `for`:
```python
for i in range(10):
    if i == 4:
        break
    print(i)

for i in range(5):
    if i % 2 == 0:
        continue
    print(i)

# iterowanie po strukturze
lista = [1, 2, 3]
for element in lista:
    print(lista)
else:
    print("Koniec!")
```
  
Pętla `while`:
```python
x = 0
while x < 5:
    print(x)
    x += 1
```
  
Instrukcja `match`  
Pozornie podobna do instrukcji `switch` z języka C, ale z większymi możliwościami dopasowania:
```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case _:
            return "Something's wrong with the internet"
```
  
Więcej przykładów i szczegółów w [dokumentacji](https://docs.python.org/3/tutorial/controlflow.html#more-control-flow-tools).
  
## Zadania  

1. Wypisz wszystkie liczby od 1 do 50, jednak jeżeli liczba jest podzielna przez:
trzy – zamiast liczby wypisz „Fizz”,
pięć – wypisz „Buzz”,
jeśli jest podzielna zarówno przez trzy i pięć - wypisz „FizzBuzz”.
2. Napisz program, który symuluje 1000 rzutów sześcienną kostką, a następnie podaje użytkownikowi ile razy wypadła dana ścianka kostki. Użyj modułu `random` (poszukaj odpowiedniej metody w [dokumentacji](https://docs.python.org/3/library/random.html#functions-for-integers)).  
3. Stwórz prostą grę polegającą na zgadywaniu przez gracza losowej liczby całkowitej z zakresu `1-100`, wygenerowanej przez komputer. Użytkownik wprowadza liczbę, a program nakierowuje gracza przez podpowiedzi, np. "Podałeś za małą/za dużą liczbę" lub w przypadku trafienia informuje o wygranej. Możesz opcjonalnie dodać warunek maksymalnie `n` prób.  
Pytanie "przy okazji": jaka jest najlepsza strategia na wygraną?
4. Dowiedz się, jak iterować pętlą `for` przez słownik, a następnie dodaj do zadania z osobami i datami urodzin wypisanie wszystkich rekordów w słowniku w formacie `'{klucz slownika} : {wartosc - data}'`.
5. Napisz program, który pyta użytkownika o dzień tygodnia i zwraca odpowiednio napis `dzien roboczy`, `weekend` lub `nieprawidlowa wartosc`.
  
# Obsługa i manipulacja napisami (typ str)

Python udostępnia bardzo bogatą bibliotekę funkcji wbudowanych, za pomocą których można manipulować łańcuchami znaków w wygodny i zwięzły sposób.

1. Tworzenie napisów
```python
s1 = "Witaj, swiecie!"
s2 = 'Mozna stosowac zamiennie pojedynczy \' lub podwójny \" cudzyslow'
s3 = """albo przechowywac 
wieloliniowy  
napis w potrojnym cudzyslowie"""
```

2. Indeksowanie napisów
```python
# indeksowanie
s1 = 'Python'
print(s[0])
print(s[-1])

# tzw. slicing - dziala rowniez na listach
s2 = 'Hello, World!'
print(s2[0:5])   # 'Hello'
print(s2[:5])    # 'Hello'
print(s2[7:])    # 'World!'
print(s2[-6:-1]) # 'World'
print(s2[0::2])  # 'Hlo ol!
```
Zwróć szczególną uwagę na znaczenie wartości podawanych w zakresach, np. ile i które indeksy zawiera zakres [0:5].

3. Modyfikowanie napisów
```python
s = 'python '
print(s.upper())  # 'PYTHON '
print(s.lower())  # 'python '
print(s.capitalize())  # 'Python '
```
```python
s = "  hello!  "
print(s.strip())   # 'hello!'
print(s.lstrip())  # 'hello!  '
print(s.rstrip())  # '  hello!'
```
```python
s1 = "Hello, world!"
print(s.replace("world", "Python"))  # 'Hello, Python!'

s2 = "apple,banana,orange"
print(text.split(","))  # ['apple', 'banana', 'orange']
```
```python
words = ["Python", "is", "fun"]
print(" ".join(words))  # 'Python is fun'
```
4. Szukanie w napisach:
```python
s = "Python is awesome"
print("Python" in s)   # True
print("Java" not in s) # True
```
```python
s = "Hello, Python!"
print(s.find("Python"))  # zwraca indeks pierwszego wystapienia lub -1 w razie braku
print(s.startswith("Hello"))
print(s.endswith("!"))
```

Więcej w [dokumentacji](https://docs.python.org/3/library/stdtypes.html#string-methods).

## Zadania
1. Napisz funkcję, która zwraca inicjały (wielkimi literami) dla podanego imienia i nazwiska.
Przykład: `print(get_initials("katarzyna marczak"))  # "KM"`

2. Napisz funkcję, która w podanym tekście cenzuruje (wygwiazdkuje) dane słowo.
Przykład: `print(censor("tekst do cenzury", "tekst"))  # "***** do cenzury"`

3. Napisz funkcję, która zliczy unikalne słowa w danym napisie. Np. dla napisu "test auto test abc" zliczy : 2 wystąpienia słowa test, 1 auto i 1 abc. Zastanów się, jakiej struktury danych najlepiej użyć do tego zadania.

4. Napisz funkcję, która poprawi zdanie tak, by zaczynało się od wielkiej litery i kończyło kropką.  
Przykład: `print(correct("popraw mnie"))  # "Popraw mnie."`

5. Napisz funkcję, która usunie powtarzające się słowa z napisu (zwróci napis bez pierwotnych powtórzeń).  
Przykład: `print(remove_duplicated_words("to to jest pewien napis napis napis do poprawy"))  # "to jest pewien napis do poprawy"
  
# Narzędzie `pip` - instalacja zewnętrznych modułów Pythona
Standardowa biblioteka Pythona posiada bardzo wiele przydatnych modułów. Jeśli potrzebujemy modułu spoza tej biblioteki, zainstalujemy go za pomocą narzędzia `pip` (https://pypi.org/).  
  
Najwazniejsze komendy `pip`:  
  
Wypisanie dostępnych modułów  
`pip list`  
  
Zapisanie modułów do pliku  
`pip freeze > requirements.txt`  
Uwaga: requirements.txt to powszechnie przyjęta konwencja przechowywania listy modułów wymaganych do uruchomienia danego programu w Pythonie.  
  
Instalacja i usuwanie modułów  
```
pip install [--user] nazwa_pakietu[==konkretna wersja]
pip install -r requirements.txt
pip uninstall nazwa_pakietu
```
