# Prognozowanie-cukrzycy-u-kobiet
**Cukrzyca** (diabetes mellitus) to przewlekła choroba metaboliczna wynikająca z zaburzonego 
wydzielania lub działania insuliny - hormonu produkowanego przez trzustkę.

Dane Światowej Organizacji Zdrowia (WHO) wskazują, że według szacunków na rok 2014 na całym świecie żyło 422 miliony dorosłych osób z cukrzycą (w porównaniu do 108 milionów w 1980 roku). International Diabetes Federation prognozuje, że do 2040 roku liczba osób z cukrzycą wzrośnie do 642 milionów. Szacunki Centers for Disease Control and Prevention sugerują, że cukrzyca i jej powikłania staną się główną przyczyną zgonów kobiet do 2040 roku, a odsetek kobiet z tą chorobą może wzrosnąć o 40 procent. Dane te podkreślają znaczenie zwiększenia świadomości na temat cukrzycy oraz potrzebę działań profilaktycznych i edukacyjnych, aby zaradzić temu problemowi na skalę globalną.

Celem pracy jest zbadanie jakości prognozowania wybranymi metodami uczenia maszynowego:
- Metoda k najbliższych sąsiadów (KNN)
- Ważona metoda k najbliższych sąsiadów (KKNN)
- Regresja logistyczna
- Liniowa analiza dyskryminacyjna (LDA)

Dane „diabetes.csv” dotyczą 768 kobiet opisanych za pomocą 9 zmiennych:
- pregnant – ilość ciąż 
- glucose - stężenie glukozy w osoczu (test tolerancji glukozy)
- pressure - rozkurczowe ciśnienie krwi (mm Hg)
- triceps - grubość fałdu skórnego tricepsa (mm)
- insulin – stężenie insuliny po 2 godzinach (mu U/ml)
- mass - wskaźnik masy ciała (masa w kg/ (wzrost w m)^2) 
- pedigree – funkcja rodowodu cukrzycy
- age – wiek (lata)
- diabetes - zmienna kategoryczna (test na cukrzycę): pos lub neg

Wyniki przeprowadzonej analizy wskazują, że istnieje związek między wiekiem, masą ciała, stężeniem glukozy we krwi oraz liczbą ciąż a ryzykiem zachorowania na cukrzycę. W miarę wzrostu tych czynników rośnie ryzyko wystąpienia tej choroby.

**Macierz błędu**

![image](https://github.com/klaudiasolek/Prognozowanie-cukrzycy-u-kobiet/assets/146526586/c7833a65-6dc2-49d2-b770-18eef64e976a)

Do oceny macierzy błędu służą parametry takie jak:
- dokładność (ang. accuracy)
- czułość (ang. sensivity)
- specyficzność (ang. specificity)

Dokładność jest miarą oceniającą jakość klasyfikacji w teście. Określa, jaka część wszystkich przeprowadzonych testów na cukrzycę została prawidłowo zaklasyfikowana. Dokładność jest stosunkiem sumy przypadków prawdziwie pozytywnych i prawdziwie negatywnych do wszystkich przypadków poddanych klasyfikacji.
Czułość jest miarą wskazującą, w jakim stopniu klasa faktycznie pozytywna została objęta wynikami pozytywnymi w teście diagnostycznym. Innymi słowy, określa procent osob, które faktycznie chorują na cukrzycę, a test diagnostyczny wykazał wynik pozytywny.
Specyficzność to miara wskazująca w jakim procencie klasa faktycznie negatywna została pokryta przewidywaniem negatywnym (procent osób zdrowych, dla których test diagnostyczny wskazuje wynik negatywny).
Wszystkie parametry (dokładność, czułość, specyficzność) powinny osiągać jak największą wartość (dążyć do 1).

**Metoda k najbliższych sąsiadów** (KNN, k-Nearest Neighbors) dla obiektu, wyznacza k jego najbliższych sąsiadów (tj. punktów o najmniejszej odległości według zadanej metryki), a następnie wyznacza 
wynik w oparciu o głos większości tych obiektów.

Zbiór uczący wyniki parametrów dla k = 3: 
- Dokładność: 84,53%
- Czułość: 89,41%
- Specyficzność: 75%

Zbiór testowy wyniki parametrów dla k = 3: 
- Dokładność: 69,48%
- Czułość: 82,97%
- Specyficzność: 48,33%

**Ważona metoda k najbliższych sąsiadów** (KKNN) jest pewnym udoskonaleniem metody k najbliższych sąsiadów. „Głosowanie” dotyczące klasyfikacji wciąż uwzględnia k sąsiadów. Waga „głosu” nie jest 
taka sama, a zależy od odległości sąsiada od klasyfikowanego obiektu.

Zbiór uczący wyniki parametrów dla k = 3: 
- Dokładność: 100%
- Czułość: 100%
- Specyficzność: 100%

Zbiór testowy wyniki parametrów dla k = 3: 
- Dokładność: 71,42%
- Czułość: 80,85%
- Specyficzność: 56,66%

**Regresja logistyczna** jest techniką regresyjną co oznacza, że jest ona zestawem narzędzi statystycznych służących do oszacowania zależności między zmiennymi. W regresji logistycznej, na 
podstawie zestawu cech ilościowych i jakościowych chcemy przewidzieć wartość zmiennej jakościowej.

Zbiór uczący wyniki parametrów: 
- Dokładność: 76,38%
- Czułość: 87,93%
- Specyficzność: 53,84%

Zbiór testowy wyniki parametrów: 
- Dokładność: 78,57%
- Czułość: 90,42%
- Specyficzność: 60%

**Liniowa analiza dyskryminacyjna** (LDA) to metoda geometryczna, która koncentruje się na znalezieniu takiego kierunku rzutowania punktów na hiperpłaszczyznę, by jednocześnie: 
– maksymalizować odległość między średnimi w grupach, 
– minimalizować wariancję wewnątrzgrupową.
Im dalej od siebie będą położone punkty centralne i im mniejszy będzie rozrzut, tym mniej pokrywać się będą ich rozkłady.
Założenia dla zmiennych ilościowych:
- równość wariancji w grupach,
- rozkład normalny w grupach.
Założenie o równości wariancji w grupach nie jest spełnione dla zmiennych: pedigree, pregnant oraz 
glucose, dlatego nie sprawdzamy drugiego założenia o rozkładach normalnych w grupach i nie wykorzystujemy LDA.

**Podsumowanie**
Najwyższą dokładność osiągnięto dla modelu KKNN na zbiorze uczącym, podczas gdy najniższą dla modelu KNN na zbiorze testowym.
**Krzywa ROC** jest narzędziem oceny jakości klasyfikatora dla różnych punktów odcięcia. Jest to graficzne przedstawienie zachowania modelu w zależności od poziomów specyficzności i czułości. Im bardziej krzywa ROC unosi się nad krzywą y = x tym lepszy jest klasyfikator. 

![image](https://github.com/klaudiasolek/Prognozowanie-cukrzycy-u-kobiet/assets/146526586/89a1cfd1-aee4-4ef7-bd03-6c50e0e88679)

Krzywa ROC dla zbioru uczącego jest wyżej nad krzywą 𝑦 = 𝑥 niż krzywa dla zbioru testowego.

![image](https://github.com/klaudiasolek/Prognozowanie-cukrzycy-u-kobiet/assets/146526586/1adf389c-3ba3-4adf-8b06-57f202145c63)

Krzywa ROC dla zbioru uczącego osiąga najlepszy możliwy poziom. Krzywa dla zbioru uczącego 
najbardziej odbiega od krzywej ROC dla zbioru testowego niż w innych metodach.

![image](https://github.com/klaudiasolek/Prognozowanie-cukrzycy-u-kobiet/assets/146526586/fafa3a6d-6c8c-4382-ba4a-f555b2842a88)

Krzywa ROC dla zbioru testowego jest wyżej niż krzywa dla zbioru uczącego.
**AUC** 
Pole pod krzywą ROC (AUC) to miara jakości klasyfikacji. Dla AUC = 0,5 klasyfikator jest losowy, a dla AUC = 1 klasyfikator jest idealny.
- AUC KNN zbiór uczący = 0,822
- AUC KNN zbiór testowy = 0,6566
- AUC KKNN zbiór uczący = 1
- AUC KKNN zbiór testowy = 0,7378
- AUC regresja liniowa zbiór uczący = 0,7089
- AUC regresja liniowa zbiór testowy = 0,7521
Wyniki pokazują, że model KKNN na zbiorze uczącym osiągnął idealne AUC wynoszące 1, co sugeruje doskonałą zdolność rozróżniania klas na tym zbiorze. Model KNN na zbiorze testowym uzyskał najniższe AUC, co może oznaczać pewien stopień niestabilności modelu na zbiorze testowym, ale wynik wciąż jest akceptowalny.
Podsumowując, analiza krzywych ROC i wyników AUC wskazuje na ogólnie dobrą jakość klasyfikacji w przypadku badanych modeli.
