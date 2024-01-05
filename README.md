# [php](http://php.ndof.org)

NDOF to format pliku do przechowywania różnych formatów danych w jednym pliku 

Można w ten sposób przechoywać także strukturę plików, 
+ w pierwszej linijce dodać JSON-a z nazwami plików i odpowiednich numerach linijek, aby ładując do aplikacji konkretne pliki za pomocą drivera nie szukać ich w systemie plkiów czy np poprzez http dla stron www 
mapowanie systemu pliku i requestów http dla cachowania danych aplikacji 

## Zastosowanie

backendowa aplikacja z frontendem w PHP mogłaby się składać z 4 plików: 

1. index.php z funkcjami i programem oraz funkcją czytania z pliku NDOF 

2. plik danych aplikacji: application.ndof 

3. user.sqlite - dane użytkownika z aplikacji 

4. compose.json - z tradycyjnym pobieraniem zależnosci dla PHP 


w przypadku zmiany techstacka- nie ma struktury, więc nie ma problemu z migracją, dane mogą być edytowane z innego projektu, gdzie masz zależność np. z submodułu, i "pakowaną" strukturę do danych aplikacji w formacie NDOF 

można też dodać skrypt synchronizujący dane bezpośrednio z jakiegoś repo, publicznego i zapisuje/dodaje te dane do pliku NDOF 

które pozostają do dyspozycji jako obiekt dostępny przez Twoją aplikację 

to mogą być różne dane zapisywalne bez białych znaków EOL, 
+ pliki binare nie będą mogłybyć załączane, gdyż istnieje ryzyko braku wsparcia dla formatów z dłuższymi liniami i specjalnymi znakami

generowanie struktury mogłoby wygladac tak: 

```
ndof <add/del> <output> <data path> <filtered files> 
```
z opcjami: add / del 

```bash
ndof app.ndof ~/www *.js *.html *.json 
```

albo ze zdalnego repo:  
```bash
ndof add app.ndof https://github.com/ndof-org/examples.git *.js *.html *.json 
```

