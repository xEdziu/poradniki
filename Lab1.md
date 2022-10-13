Lekcja 1 - Poczatki
==================================================
1. napiszmy najprostrszy program:
```
int main() {
	return 0;
}
```

ale czemu returnujemy numer w programie co nic nie robi?

Returnowany numer z funkcji main mowi nam o kodzie bledu, ktory bedzie przekazany systemowi operacyjnemu. Dzieki niemu mozna konkretnie dowiedziec sie co poszlo nie tak.
Error code 0 oznacza ze nie bylo zadnych bledow i program zadzialal jak mial.

dobra, do kompilacji.
Najprosciej jest mozna to zrobic komenda:
```
make <nazwa pliku bez rozszerzenia>
```
albo
```
g++ <nasz plik> -o <nazwa jaka chcemy dac naszemu programowi>
```
to -o to jest tak zwana flaga. Mozna ich uzywac by powiedziec programowi aby sie zachowal z pewnien sposob.
-o (output) mowi mu aby nazwa pliku byla jaka chcemy. Inny przyklad to jest flaga -v ktora czesto oznacza version albo verbose.
Sa jeszcze flagi jako slowa ktore sie zaczynaja z --. Na przyklad --version.

2. Niepotrzebne jebanie sie z kompilatorem
procesow kompilacji nie chce mi sie pisac xD (oraz to jest kompletnie niepotrzebne, w tych czasach kompilery wszystko robia to same). Adrian w swoim poradniku to opisal.

3. Includowanie innych plikow w nasz program

nasz program bedzie sie skladac z dwoch plikow:
- main.cpp
- func.h

w func.h napiszemy nasza funkcje, ale uzyjemy jej z main.cpp.

najpierw zacznijmy od func.h
```
int add(int a, int b) {
	return a+b;
}
```
dobra co tu sie stalo:
 - funckja jest zdefiniowana jako int, czyli ma zwracac intiger
 - to w nawiasie to ja nasze argumenty funkji. Sa to dane ktore przekarzemy funkcji podczas jej wywolywania. Jak widac obie te dane maja byc int'ami
 - ``return a+b`` po prostu zwraca well, a+b. ``return`` ogolnie konczy wykonywanie funkcji.
  Czyli jesli wywolamy ``return`` kod w tej funkcji po return po prostu nie bedzie wykonany.

ok czas na main.cpp

```
#include <iostream>
#include "func.h"

int main() {
	int a = 4;
	int b = 5;
	std::cout << add(a,b) << std::endl;
	return 0;
}
```

ok wiec:
 - ``#include`` importuje nam inne pliki. wersja z <> bedzie szukac systemowych bibliotek, a wersja z "" bedzie szukac po folderach z miejsca, gdzie jest nasz plik
 czyli mozemy wrzucic nasz func.h w nowego folderu amogus i wtedy damy #include "amogus/func.h".
 - ``int main`` deklaracja naszej glownej funkcji. Jest ona i TYLKO ona wykonywana podczas dzialania programu. Jakikolwiek kod ktory nie ma jakiegos polaczenia do main bedzie ignorowany. Moze byc tylko jednak funkcja main per program.
 - ``int a, int b`` - deklarujemy nowe zmienne o nazwie a i b o danych wartosciach.
 - ``std::`` - jest to pokazanie z jakiej biblioteki kompiler ma wziasc pewne rzeczy. Teraz bierzemy z biblioteki std (standard). Mozna tez uzyc ``using namespace <biblioteka>;`` we funkcji gdzie bedziemy duzo uzywac tej biblioteki
 UWAGA: uzywanie ``namespace`` poza funkcja zrobi go globalnym, jednak jest to mocno nierekomendowane i ogolnie sie tak nie robi. Moze powodowac problemy jak zaczniemy uzywac wiecej bibliotek
 - ``cout`` jest stream danych jakie beda wyswietlone na standardowym output-cie. << mowi zeby wlozyc dane do tego streamu.
 - ``add(a,b)`` i tutaj wywolujemy nasz funkcje ktora napisalismy w innym pliku! Przekazujemy jej nasze zmienne a i b. Zwroci ona nam sume naszych liczb, ktora bedzie wlozona do streamu cout
 - ``endl`` - end line, selfexplanatory, mozna tez dac ``"\n"`` - newline
 - ``return 0`` tu jak wczesniej wspomnialem potwierdzamy ze nasz program wykonal sie poprawnie

czas to zkompilowac
 - nie bedzie sie to roznic od poprzedniego przykladu
 poprostu ``make main`` albo ``g++ main.cpp -o sus``.
 - mozna uruchomic program dajac ``./sus``
