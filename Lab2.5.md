Pobieranie argumentow z konsoli
===============================

Czasami chcemy pobrac argumenty od uzytkownika, na przyklad by podac jakas wartosc badz specyfikowac zachowanie programu np. te flagi o ktorych pisalem poprzednio w Lab2.
Mozna to zrobic w miare latwo, ale bedziemy musieli dodac pare rzeczy do definicji funkcji ``main``:
```
		array, ktory trzyma wszystkie
		argumenty podane przez uzytkownika
		po kolei jako string.
                         |
 argc (argument count)   |
 ilosc argumentow, jakie |
 uzytkownik podal        |
	    |            |
           vvv          vvv
int main(int argc, *char argv[]) {
	
}
```

dobra mamy teraz ilosc argumentow oraz array z naszymi argumentami, z ktorymi mozemy robic juz co chcemy. !!!WAZNE!!! argumentem 0, czyli pierwszym jest zawsze nazwa execa.
Nie zabardzo wiem co dalej tu napisac bo w sumie to wszystko, podam wiec pare najprostrzych przykladow programow co to uzywaja:
### program ktory wypisze wszystkie nasze argumenty
ten program sprawdza czy podalismy cokolwiek, po czym wypisze nasze argumenty. Nie wypisze on nazwy execa, ktora niby miala byc pierwszym argumentem
poniewaz w naszej petli for mamy int i = 1; czyli zaczniemy wypisywac z array-a od pozycji 1 (pierwsza rzecz w array-ach ma index 0).

uzylismy tez ``using namespace std;`` zebysmy nie musieli pisac std:: przed kazdym cout i endl. W Lab2 napisalem ze uzywanie tego ogolnie w calym programie to zly practice, dlatego uzywamy teraz w main, czyli bedzie to dzialac tylko w obrabie main(co tez nie jest swietne bo to jest main, ale w tak malym programie to nie ma znaczenia)
```
#include <iostream>

int main(int argc, char *argv[]) {
	using namespace std;
	
	if(argc < 2){ // sprawszamy czy sa jakies argumenty. Sprawdzamy do dwojki poniewaz nazwa execa to jest jeden argument, czyli teorytyczny brak argumentow to jeden argument
		cout << "Please provide at least one argument" << endl; //jak nie ma zadnych argumentow, to opieprzyc uzytkownika,
		return 1; //oraz skonczyc dzialanie z kodem bledu.
	}
	
	for(int i = 1; i < argc; i++) { //argv jest to troche 'specjalny' array, wiec nie mozemy uzyc foreach.
		cout << argv[i] << endl;
	}
	
	return 0;
}
```

### program z uzywalna flaga.
wezmy poprzedni program ale dodajmy do niego mozliwosc uzycia flagi ``-h``. -h zwykle ozacza help, wiec mozemy zmienic zachowanie programu z przedrzezniania nas na wyslietlenie opisu.
wiec dodajmy jednego if-a, ktory sprawdzi, czy nasz drugi argument jest ``-h``, i jesli jest, to zmienmy zachowanie programu.
```
	...
		return 1;
	}

	string arg1 = "-h"; //nowa zmienna typu string. !! C nie ma natywnego wsparcia dla stringow, wiec tam trzeba bedzie zincludowac biblioteke string
	if(argv[1] == arg1) {
		cout << "this program is utterly useless :))" << endl; //wyswietl nasz 'help' message
		return 0; //zakoncz dzialanie programu.
	}

	for(int i = 1; i < argc; i++) {
	...
```
