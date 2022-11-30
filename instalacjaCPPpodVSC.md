# Konfiguracja kompilatora C++ w Visual Studio Code
### Autor: Adrian Goral

1. Zainstaluj Visual Studio Code
   
2. Zainstaluj rozszerzenie C/C++ dla Visual Studio Code
   
   ![image](https://user-images.githubusercontent.com/50357817/204749296-1d6c67a9-08f5-4256-b5b4-90653a2c667c.png)

3. Zainstaluj program [MSYS2](https://github.com/msys2/msys2-installer/releases/download/2022-06-03/msys2-x86_64-20220603.exe)

4. Uruchom MSYS2 i zainstaluj kompilator C++:
   ```bash
   pacman -S --needed base-devel mingw-w64-x86_64-toolchain
   ```
   ![image](https://user-images.githubusercontent.com/50357817/204749805-b9dffc58-a0a3-4577-9a31-28ba50fa221d.png)
   
5. Dodać ścieżkę do kompilatora do PATH (zmienna środowiskowa)
   - Wpisz w wyszukiwarce `Zmienne środowiskowe` i wybierz `Edytuj zmienne środowiskowe dla Twojego konta`
   - Kliknij `Zmienne środowiskowe...`
   - Zaznacz `Path` i kliknij `Edytuj...`
   - Dodaj ścieżkę do kompilatora: `C:\msys64\mingw64\bin` lub ściężkę do folderu, w którym został zainstalowany kompilator
   - Klknij `OK` - NIe zamykaj okna `Zmienne środowiskowe` poprzez ```X```!
  
6. Zrestartuj Visual Studio Code
   
7. Sprawdź wersję kompilatora w Wierszu poleceń
   - Wpisz w wyszukiwarce `Wiersz poleceń`
   - Wpisz `g++ --version`
  
   ![image](https://user-images.githubusercontent.com/50357817/204750716-a008712a-d298-41a3-ae44-337a3e6d3904.png)

8. Utwórz plik `hello.cpp` i wpisz w nim kod:
   ```cpp
    #include <iostream>
    int main()
    {
        std::cout << "Hello World!\n";
    }
    ```
9.  Kliknij przycisk `Play` w prawym górnym rogu okna
    
   ![image.png](https://code.visualstudio.com/assets/docs/cpp/playbutton/run-play-button.png)

10. Wybierz następującą opcję:

    ![image](https://code.visualstudio.com/assets/docs/cpp/playbutton/select-gcc-compiler.png)

11. Tylko raz zostaniesz poproszony o wykonanie tej czynności. Każde kolejne uruchomienie programu będzie wykonywane automatycznie.
