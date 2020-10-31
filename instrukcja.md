# Lekcja 1 – Markdown lekki język znaczników

## Spis treści

Lekcja 1 – Markdown lekki język znaczników....................................................................................1  
Wstęp...............................................................................................................................................1  
Podstawy składni.............................................................................................................................3  
Definiowanie nagłówków...........................................................................................................3  
Definiowanie list.........................................................................................................................4  
Wyróżnianie tekstu......................................................................................................................4  
Tabele..........................................................................................................................................5  
Odnośniki do zasobów................................................................................................................ 5  
Obrazki........................................................................................................................................5  
Kod źródłowy dla różnych języków programowania.................................................................5  
Tworzenie spisu treści na podstawie nagłówków.......................................................................6  
Edytory dedykowane.......................................................................................................................7  
Pandoc – system do konwersji dokumentów Markdown do innych formatów...............................8  
Lekcja 2 – Git – system kontroli wersji................................................................................................9  
Git - podstawowe cechy...................................................................................................................9  
Idea pracy:........................................................................................................................................9  
Git – tworzenie pustego archiwum lokalnego...............................................................................11  
Zadania do wykonania na punkty.......................................................................................................21  
Zadanie 1 – 2pkt............................................................................................................................21  
Zadanie 2 – 4pkt............................................................................................................................21  
Zadanie 3 - 4pkt.............................................................................................................................21  

## Wstęp

Obecnie powszechnie wykorzystuje się języki ze znacznikami do opisania dodatkowych informacji
umieszczanych w plikach tekstowych. Z pośród najbardziej popularnych można wspomnieć o:

1. **html** – służącym do opisu struktury informacji zawartych na stronach internetowych,  

2. **Tex** (Latex) – poznany na zajęciach język do „profesjonalnego” składania tekstów,  

3. **XML** ( _Extensible Markup Language)_ - uniwersalnym języku znaczników przeznaczonym do
    reprezentowania różnych danych w ustrukturalizowany sposób.



Przykład kodu html i jego interpretacja w przeglądarce:  

<img style="float:right" src="1.png">

<\!DOCTYPE **html**>  
<**html**>  
<**head**>  
<**meta** <span style="color:darkblue">charset</span><span style="color:lighgreen">=</span><span style="color:orange">"utf-8"</span><span style="color:lightgreen"> /</span>>  
\<<span style="color:darkblue">title</span>>Przykład\<<span style="color:lightgreen">/</span><span style="color:darkblue">title</span>>  
<<span style="color:lightgreen">/</span>**head**>  
<**body**>  
<**p**> Jakiś paragraf tekstu<<span style="color:lightgreen">/</span>**p**>  
<<span style="color:lightgreen">/</span>**body**>  
<<span style="color:lightgreen">/</span>**html**>  


Przykład kodu Latex i wygenerowanego pliku w formacie pdf:  

<img style="float:right" src="2.png">

\\<span style="color:darkred">documentclass</span>[]{<span style="color:darkblue">letter</span>}  
\\<span style="color:darkred">usepackage</span>{<span style="color:darkblue">lipsum</span>}  
\\<span style="color:darkred">usepackage</span>{<span style="color:darkblue">polyglossia</span>}  
\\<span style="color:darkred">setmainlanguage</span>{<span style="color:darkblue">polish</span>}  
\\<span style="color:blue">**begin**</span>{<span style="color:blue">**document**</span>}  
\\<span style="color:blue">**begin**</span>{<span style="color:blue">**letter**</span> }{<span style="color:blue">**Szanowny Panie XY**</span> }  
\\<span style="color:darkred">address</span>{<span style="color:darkblue">Adres do korespondencji</span>}  
\\<span style="color:darkred">opening</span>{}  
\\<span style="color:darkred">lipsum</span>[2]  
\\<span style="color:darkred">signature</span>{<span style="color:blue">Nadawca</span>}  
\\<span style="color:darkred">closing</span>{<span style="color:blue">Pozdrawiam</span>}  
\\<span style="color:blue">**end** {<span style="color:blue">**letter**</span>}  
\\<span style="color:blue">**end** {<span style="color:blue">**document**</span>}  

Przykład kodu XML – fragment dokumentu SVG (Scalar Vector Graphics)  
<img style="float:right" src="12.png">
<\!DOCTYPE **html**>  
<**html**>  
<**body**>  
\<svg <span style="color:darkblue">height</span><span style="color:lightgreen">=</span>"100" <span style="color:darkblue">width</span><span style="color:lightgreen">=</span>"100">  
 \<circle cx<span style="color:lightgreen">=</span><span style="color:orange">"50"</span> cy<span style="color:lightgreen">=</span><span style="color:orange">"50"</span> r<span style="color:lightgreen">=</span><span style="color:orange">"40"</span> stroke<span style="color:lightgreen">=</span><span style="color:orange">"black" </span>stroke-<span style="color:darkblue">width</span><span style="color:lightgreen">=</span><span style="color:orange">"3"</span> fill<span style="color:lightgreen">=</span><span style="color:orange">"red" </span><span style="color:lightgreen">/</span>>  
\<<span style="color:lightgreen">/</span>svg>  
<<span style="color:lightgreen">/</span>**body**>  
<<span style="color:lightgreen">/</span>**html**>  


W tym przypadku mamy np. znacznik np. \<circle> opisujący parametry koła i który może być
właściwie zinterpretowany przez dedykowaną aplikację (np. przeglądarki www).

Jako ciekawostkę można podać fakt, że również pakiet MS Office wykorzystuje format XML do
przechowywania informacji o dodatkowych parametrach formatowania danych. Na przykład pliki z
rozszerzeniem _docx_ , to nic innego jak spakowane algorytmem zip katalogi z plikami xml.


<span style="color:lightgreen">$unzip</span><span style="color:#871F78"> -l **test**</span> .docx  
Archive:<span style="color:#871F78"> **test**</span> .docx  
Length <span style="color:#D25DC1">**Date</span> Time** Name  
\--------- ---------- ----- ----  
573 2020-10-11 18:20 _rels **/** .rels  
731 2020-10-11 18:20 docProps **/** core.xml  
508 2020-10-11 18:20 docProps **/** app.xml  
531 2020-10-11 18:20 word **/** _rels **/** document.xml.rels  
1421 2020-10-11 18:20 word **/** document.xml  
2429 2020-10-11 18:20 word **/** styles.xml  
853 2020-10-11 18:20 word **/** fontTable.xml  
241 2020-10-11 18:20 word **/** settings.xml  
1374 2020-10-11 18:20 **[** Content_Types **]** .xml  

Wszystkie te języki znaczników cechują się rozbudowaną i złożoną składnią i dlatego do ich edycji
wymagają najczęściej dedykowanych narzędzi w postaci specjalizowanych edytorów. By
wyeliminować powyższą niedogodność powstał **Markdown** - uproszczony język znaczników
służący do formatowania dokumentów tekstowych (bez konieczności używania specjalizowanych
narzędzi). Dokumenty w tym formacie można bardzo łatwo konwertować do wielu innych
formatów: np. html, pdf, ps (postscript), epub, xml i wiele innych. Format ten jest powszechnie
używany do tworzenia plików README.md (w projektach open source) i powszechnie
obsługiwany przez serwery git’a. Język ten został stworzony w 2004 r. a jego twórcami byli John
Gruber i Aaron Swartz. W kolejnych latach podjęto prace w celu stworzenia standardu rozwiązania
i tak w 2016 r. opublikowano dokument <span style="color:#871F78"><ins>RFC 7764</ins></span> który zawiera opis kilku odmian tegoż języka:

- CommonMark,
- GitHub Flavored Markdown (GFM),
- Markdown Extra.

## Podstawy składni

Podany link: <ins>https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet </ins>zawiera opis
podstawowych elementów składni w języku angielskim. Poniżej zostanie przedstawiony ich krótki
opis w języku polskim.

### Definiowanie nagłówków

W tym celu używamy znaku kratki

Lewe okno zawiera kod źródłowy – prawe -podgląd przetworzonego tekstu

<img style="float:center" src="3.png">  

### Definiowanie list

<img style="float:center" src="4.png">    

Listy numerowane definiujemy wstawiając numery kolejnych pozycji zakończone kropką.

Listy nienumerowane definiujemy znakami: *,+,-

### Wyróżnianie tekstu

<img style="float:center" src="5.png"> 

### Tabele

<img style="float:center" src="6.png">

Centrowanie zawartości kolumn realizowane jest poprzez odpowiednie użycie znaku dwukropka:

### Odnośniki do zasobów

[odnośnik do zasobów](www.gazeta.pl)

[odnośnik do pliku](LICENSE.md)

[odnośnik do kolejnego zasobu][1]

[1]: [http://google,com](http://google,com)

**Obrazki**

![alt text](https://server.com/images/icon48.png "Logo 1") – obrazek z zasobów
internetowych  

![](logo.png) – obraz z lokalnych zasobów  

### Kod źródłowy dla różnych języków programowania  

<img style="float:center" src="7.png">

### Tworzenie spisu treści na podstawie nagłówków  

<img style="float:center" src="8.png">

## Edytory dedykowane

Pracę nad dokumentami w formacie Markdown( rozszerzenie md) można wykonywać w
dowolnym edytorze tekstowym. Aczkolwiek istnieje wiele dedykowanych narzędzi

1. Edytor Typora - https://typora.io/
2. Visual Studio Code z wtyczką „markdown preview”

<img style="float:center" src="9.png">

## Pandoc – system do konwersji dokumentów Markdown do

## innych formatów

Jest oprogramowanie typu open source służące do konwertowania dokumentów
pomiędzy różnymi formatami.

Pod poniższym linkiem można obejrzeć przykłady użycia:

https://pandoc.org/demos.html

Oprogramowanie to można pobrać z spod adresu: https://pandoc.org/installing.html

Jeżeli chcemy konwertować do formatu latex i pdf trzeba doinstalować oprogramowanie
składu Latex (np. Na windows najlepiej sprawdzi się Miktex https://miktex.org/)

Gdyby podczas konwersji do formatu pdf pojawił się komunikat o niemożliwości
znalezienia programu pdflatex rozwiązaniem jest wskazanie w zmiennej środowiskowej
PATH miejsca jego położenia

<img style="float:center" src="10.png">

<img style="align:center" src="11.png">

Pod adresem (https://gitlab.com/mniewins66/templatemn.git) znajduje się przykładowy plik
Markdown z którego można wygenerować prezentację w formacie pdf wykorzystując
klasę latexa beamer.

W tym celu należy wydać polecenie z poziomu terminala:

$pandoc templateMN.md -t beamer -o prezentacja.pdf
