Warunki i petle
===============

## Instrukcje warunkowe - if-y

``if`` to w miare prostu koncept do ogarniecia. Jesli cos jest prawda, to wtedy kod w if-ie bedzie wykonany jesli nie, to zostanie pominiety.
Przyklad:
```
if (true) {
	ten kod zostanie wykanany
}
------------------------
if (false) {
	ten kod zostanie pominiety
}
```

if dziala tylko na bool-inach. Czyli akceptuje tylko true albo false. Piszac ``5 == 5`` mozna to traktowac jako operacja ktora zwraca boolean (w tym przypadku true, no bo jakby 5 jest rowne 5).

## Operatory if-a
### jest pare opcji by porownac rzeczy w if-ie
- ``==``  rowne. !!WAZNE!! zwroccie uwage ze sa to dwa =. Czesty blad polega na tym ze ktos daje = rowna sie.
	
	```
	int a = 69;
	if(a == 69) {
		bedzie wykonane
	}
	```

- ``!=``  nie rowne.
	```
	int a = 420;
	if(a != 420) {
		bedzie pominiete
	}
	```

- ``>``  wieksze.
	```
	int a = 2;
	if( a > 1 ) {
		wykonane
	}
	```

- ``<``  mniejsze
	```
	int a = 56;
	if( a < 40 ){
		pominiete
	}
	```

- ``>=``  wieksze badz rowne. Kolejnosc znaku > i = ma znaczenie, zawsze najpierw jeden z <, > i potem znak =.
	```
	int a = 4;
	if(a >= 4){
		wykonane
	}
	a++ //zwiekszamy a o jeden czyli teraz ma 5. a i przy okazji //oznacza komentarz, czyli cokolwiek po // bedzie ignorowane przez kompilator.
	if(a >= 4){
		wykonane
	}
	```

- ``<=``  mniejsze badz rowne
	```
	int a = 5;
	if(a <= 5) {
		wykonane
	}
	a-- //odejmujemy jeden od a.
	if(a <= 5) {
		wykonane
	}
	```

- ``===``  troche bardziej zaawansowane, oznacza rowne oraz tego samego typu, czyli na przyklad 32 bitowy intiger razem z 32 bitowym intiger bedzie jako true ale juz 64 bitowy z 32 bitowym juz false.
- ``!`` - not. Neguje wyrazenie. Przydatne jak chcemy zrobic cos jesli cos innego jest nieprawda. Wezmy przyklad z wczesniej: ``5 == 5`` zwraca true, ale ``! 5 == 5`` juz zwraca false.
	```
	int a = 5;
	if( ! a == 5 ){
		pominiete
	}
	if( ! a == 3 ) {
		wykonane
	}
	```
- `` ``  doslownie brak operatora. Dziala tylko na boolean-ach. uzywa sie to w sposob tak jak wyzej, czyli
	```
	bool sus = true;

	if(sus) {
		bedzie wykonane
	}
	//przyklad z !
	if( ! sus ) {
		pominiete
	}
	```
#### oczywiscie mozna porownywac wiecej typow niz int-y.
	```
	float a = 1.69;
	if( a >= 1.69 ) {
		wykonane
	}
	char b = 'r';
	if( ! b == 'r' ) {
		pominiete
	}
	``` 
#### !!! porownywanie float (i double) znakiem == niekoniecznie dziala ze wzgledu jak komputery radza sobie z floating point liczbami. Jest to skompikowane i nie bede tlumaczyc tego tutaj
### and i or
zamiast pisac pare if-ow  po kolei mozna uzyc ``&&`` (and) oraz ``||`` (or). ``&&`` robi ze WSZYTKIE warunki musza byc spelnione, a ``||`` tylko jeden musi byc.
- skladnia ``&&``
```
	int a = 4;
	if( a > 3 && a < 5 ){
		wykona sie
	}
	if( a > 1 && a < 4 ) {
		pominiete
	}
	//mozna oczywiscie uzyc tego wiele razy
	if( a > 1 && a <= 6 && a != 3 ){
		wykona sie
	}
```
- skladnia ``||``
```
	int a = 7;
	if( a == 7 || a == 8 ){
		wykona sie
	}
	if( a > 3 || a < 1 || a == 2 ) {
		wykona sie
	}
	if( a < 0 || a == 3 || a > 9 ) {
		pominiete
	}
```
### else
else tez jest prosty. Jesli warunek w poprzednim if wyszedl false, czyli kod w tym if-ie zostal pominiety, to kod w blocku else zostanie wykonany.
```
	int a = 4;
	if(a >= 5){
		pominiete
	} else {
		wykonane
	}
	---------------------
	int b = 1;
	if(b <= 2){
		wykonane
	} else {
		pominiete
	}
```
# Petle
petle sa to funkcje, ktore beda wykonywac kod zawarty w ich blocku (``{}``) okreslona ilosc razy. Jest pare roznych petli, wszystkie sa podobne ale niektore jest lepsze w pewnych sytuacjach.
### for
- ``for`` petla for ma dwa uzytki. Jeden jest zrobienie najprostrzej petli ktora wykona sie x ilosc razy. Kolejna bardzo uzyteczna to jest zloopawanie sie po zawartosci array-a(znana jako foreach).
Gdy chcemy uzyc for do zrobienia petli ktora sie powtorzy pewna ilosc razy, for przyjmuje wtedy 3 argumenty separowane ``;``. pierwszym jest kod ktory bedzie wykonany tylko raz przez zaczeciem petli, drugim argumentem jest warunek, ktory jak jest spelniony to petla dziala,
a trzecim argumentem jest kod ktory bedzie wykonywany co kazda iteracja petli. Przyklad:

```
		zwiekszamy i o jeden
		co kazda iteracja petli
                         |
    loopujemy dopuki i   |
    jest mniejsze lub    |
    rowne 10       |     |
                   |     |
definiujemy nowy   |     |
int na poczatku    |     |
petli   |          |     |
       vvv        vvv   vvv
for(int i = 0; i <= 10; i++) {
	ten kod zostanie wykonany 10 razy
}
```
### foreach
jak chcemy uzyc for aby zrobic operacje na kazdej rzeczy, ktora znajduje sie w array-u, to do for-a musimy podac nazwe zmiennej ktora bedzie sluzyc jako
zastepcza nazwa dla naszej rzeczy w array-u oraz podac array przez ktorego chcemy zloopawac. for bedzie zmieniac ta zmienna co kazda iteracja na nastepna rzecz w array-u. Przyklad:

```
int array[] = {1,2,3,4,5,6};
int sum_of_things = 0;

for(int i : array) {
	std::cout << i << std::endl; //wyswietli czym akurat teraz jest i.
	sum_of_things += i; //doda do sum_of_things wartosc i, ktora robi jako akurat uzywana rzecz w array-u
}

std::cout << sum_of_things << std::endl;
```
### while
- ``while`` petla ktora dziala az jej warunek jest spelniony i tyle w sumie.
```
int a = 0;
while( a <= 5 ) {
	a++;
}
```
tutaj while dziala dopuki a jest mniejsze niz 5. Wazne jest aby jakos manipulowac zmienna ktora jest w warunku, poniewaz latwo mozna stworzyc nieskonczona petla:
```
int a = 0;
while( a <= 5 ) {
	kod bedzie wykonywany w nieskoczonosc, program 'utknie' w tej sytuacji
}
```
chociaz czasami nieskonczona petla jest uzyteczna, najlatwiej sa zrobic tak:
```
while(true) {
	kod
}
```
### do while
- ``do; while`` mniej wiecej to samo co ``while``, ale kod w petli jest wykonywany zanim warunek na petle jest rozpatrzony. Uzyteczne jak chcemy by kod sie wykonal conajmniej raz nie wazne co. Przyklad:

```
int a = 0;
do {
	a++;
} while(a <= 5); //bedzie wykonane 5 razy
```
Ten przyklad pokazuje skladnie ``do; while`` ale nie pokazuje jej uzytecznosci wiec:
```
//uzywajac zwyklego while:
int a = 5;
while(a < 5) {
	ten kod bedzie kompletnie pominiety, gdzyz a nie jest mniejsze od 5.
}
//to samo ale z do while:
do {
	ten kod bedzie wykonany przed sprawdzeniem warunku, wiec bedzie wykonany
} while(a < 5) //tutaj dopiero sprawdzamy warunek, ktory w tym przypadku zatrzyma petle, ale nasz kod zostal wykonany raz pomimo niespelnionego warunku.
```

