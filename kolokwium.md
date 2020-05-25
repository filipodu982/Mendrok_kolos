[toc]



# Kolokwium

1. Bode, Nyquist, analityczny zapas stabilności
2. MGP, wzmocnienia do określonych położeń
3. Kompensatory
4. PID, dobór optymalny i suboptymalny w oparciu o $T_s$



### 1. Charakterystyki Bodego, Nyquista, zapas stabilności

#### Char. Nyquista

- Mamy transmitancję z rów. char. w mianowniku
- Wszystko się dzieje w **Układzie otwartym**
- Zamiast s podstawiamy $i\omega$ i obliczamy taką postać transmitancji. Będzie to wymagać mnożenia przez sprzężenie żeby się pozbyć z mianownika tego urojonego
- Trzeba wyłuskać z tego $Im(\omega)\ i\ Re(\omega)$ 
- Następnie budujemy sobie tabelę z charakterystycznymi omegami - 0, kiedy Re i Im są równe zero (miejsca przecięcia z osiami) , nieskończoność i sprawdzamy w tych $\omega$ jakie są wartości Im i Re
- Te miejsca posłużą nam do narysowania wykresu. Po prostu prowadzimy wykres przez odpowiednie punktu
- Następnie by zbadać zapas fazy i zapas wzmocnienia badamy ten wykres
  - Zapas fazy to kąt jaki tworzy punkt przecięcia wykresu z kołem jednostkowym z osią Im
  - Zapas wzmocnienia to miejsce przecięcia wykresu z osią Re.
- Zapas stabilności ![image-20200524174820902](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524174820902.png) 

#### Char. Bodego

- Transmitancje musimy przekształcić do postaci $\frac{K}{(T_1s + 1)(T_2s+1)}$ 
  - Jest to bardzo istotne, bo najczęściej transmitancja jest w postaci z biegunami a nie stałymi czasowymi. Jak będziemy kombinować z taką formą, to Bode nie wyjdzie, bo wyciąganie przed nawias odpowiednich współczynników doprowadzi do $K$, które jest bardzo istotne
- Z postaci tej transmitancji znamy tez bieguny układu. $p_1 = \frac{1}{T_1}$ itd. Te bieguny są ważne, bo Bodego rysujemy biorąc pod uwagę tabelkę
- ![img](https://scontent-frt3-1.xx.fbcdn.net/v/t1.15752-9/95919333_281018369584712_2070438918326583296_n.jpg?_nc_cat=102&_nc_sid=b96e70&_nc_oc=AQnwSR-B4HAdEQzIAuIBEUf5-KaUEH1mdjsc5EePv4jhbIG0gqF09CoA0eodbZQNolc&_nc_ht=scontent-frt3-1.xx&oh=ac25b609f7e04a68107478fcf387d82a&oe=5EEEAE36) gdzie n to krotność bieguna

---



### 2. MGP

- Wykres MGP dotyczy pętli zamkniętej, ale wykreślamy go dla układu otwartego.

- W przeciwieństwie do bodego tu chcemy mieć inną formę transmitancji 

- $\frac{K_o(s+z_1)}{(s+p_1)(s+p_2)}$

- $K_o$ to współczynnik czułości statycznej. Jego zmiana generuje własnie linie pierwiastkowe

- Algorytm MGP

  1. Zera i bieguny

  2. Liczba odgałęzień - liczba gałęzi jest równa liczbie biegunów układu otwartego

  3. MGP na Re - patrzymy na ilość biegunów i zer po prawej stronie punktu próbnego. Jeśli jest nieparzysta to pkt należy do MGP

  4. Punkty początkowe i końcowe - MGP zaczyna się w biegunach a kończy w zerach. Gdy mamy mniej zer to wtedy MGP dąży do $\infty$ wzdłuż Re lub jakiś asymptot

  5. Asymptoty MGP

     - Jeżeli MGP posiada asymptoty to ich kąt nachylenia:

       $\gamma_a = \frac{(2m+1)\pi}{u+n-v}$ gdzie $u+n=liczba\ biegunow$ $v = liczba\ zer$ 

       Asymptoty te przecinają się w punkcie:

       $\sigma_a = \frac{\sum p_k - \sum z_k}{u+n-v}$

       Gdzie $\sum p_k$ to suma **wartości** biegunów a $\sum z_k$ to **suma wartości** zer. Reszta jak wyżej

  6. Punkt rozejścia i **zejścia** MGP

     - Są 2 sposoby na wyznaczenie tego. Sposób 1 polega na sprawdzeniu warunku argumentów, ale ta metoda **nie działa gdy mamy bieguny sprzężone**

       $-\frac{1}{r_{p0}} + \frac{1}{r_{p1}} - \frac{1}{r_{z1}}=0$ Równanie to rozwiązujemy metodą prób i błędów dla spodziewanego punktu rozgałęzienia

     - Sposób 2 polega na tym, że w punkcie rozgałęzienia **musi** wystąpić podwójny pierwiastek rzeczywisty. Istnieje twierdzenie, które mówi, że jeśli występuje podwójny pierwiastek, to pochodna równania też się zeruje. Finalnie:

       $L'M - LM' = 0$ To równanie także metodą prób i błędów na zasadzie wyliczenia tego równania na $s$ i podstawianiu konkretnych wartości i sprawdzaniu czy jesteśmy blisko czy daleko. Z dokładnościa do 2 miejsc po przecinku

  7. Kąty wyjścia MGP z **pary biegunów sprzężonych**

     - Przepisujemy warunek argumentu by wyizolować ten konkretny kąt

       $\phi_{wj} = \sum \psi_{ij} - \sum \phi_{ij} + (2m+1)\pi$

       Gdzie $\sum \psi_{ij}$ to suma **kątów** między danym biegunem a zerami, a $\sum \phi_{ij}$ to suma **kątów** między danym biegunem a innymi biegunami. Ten **kąt** to chodzi o kąt, który tworzony jest z osią Re.

  8. Kąty wejścia do **zer**

     - Analogicznie, przepisujemy ten warunek

       $\psi_{wj} = \sum \phi_{kj} - \sum \psi_{kj} - (2m+1)\pi$ 

  9. Pkt. przecięcia MGP z Im.

     - Wartość $K_o$ w tym punkcie określa **granicę stabilności**. By to znaleźć należy wyznaczyć kryterium Routha.

     - Zamykamy pętle sprzężenia zwrotnego **wraz z dodatkowym parametrem K** 

     - Wypełniamy tablicę Routha dla rów. char.

     - Dla $s^1$ szukamy takiej wartości tego K, dla której wyzeruje się cały wiersz. 

     - Tą wartość K wstawiamy do $s^2$ dzięki czemu wyznaczymy pierwiastki, gdzie MGP przetnie oś urojonych

     - Dzięki czemu rysujemy ostateczny MGP, a jak chcemy poznać wzmocnienie w tym pkt. przecięcia to warunek modułu.

     - Warunek modułu

       $K_o = r_{p0}^n \frac{\Pi r_{pk}}{\Pi r_{zi}}$ 

       Jeśli nie ma zer, to w mianowniku 1

       

---



### 3. Kompensatory

- Kompensator to taki element, który łączymy szeregowo z układem w celu poprawy jego odpowiedzi

- Kompensator posiada jedno zero i jeden biegun

- Wzór:

  $C(s) = K \frac{(s+z_k)}{(s+p_k)}$ 

  - Kompensator wyprzedzający $|z| < |p|$
  - Kompensator opóźniający $|z| > |p|$ 

- **Kompensator wyprzedzający**

  - Przyspiesza działanie układu

  - $C(s) = \frac{Ts+1}{T\alpha s+ 1}\ gdzie\ \alpha < 1$

  - Parametry $\alpha\ i\ T$ dobiera się tak aby uzyskać dla układu **otwartego** określony zapas fazy.

  - Dla układów z trzema biegunami rzeczywistymu zero umiejscawia się jak najbliżej środkowego bieguna

  - Biegun obiektu sterowania przesuwa się na maxa w lewo, ale nie więcej niż 10 razy. Wtedy $\alpha = 0.1$ 

  - *Maksymalne przesunięcie fazy w przód* 

    $\phi_m = arcsin \frac{1-\alpha}{1+\alpha}$

    dla częstotliwości

    $\omega_m = \frac{1}{T\sqrt{\alpha}}$

  - Maksymalne wzmocnienie dla częstotliwości $\omega_m$ jest połową wzmocnienia początkowego i końcowego:

    $G_m(\omega_m) = -20log(\sqrt{\alpha}) = -10log\alpha$

  - Do odczytu własności można użyć takiej tabeli:

    ![image-20200524192325843](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524192325843.png) 

  - **Projektowanie w oparciu o Bodego** 

    ![image-20200524192447311](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524192447311.png) 

  - Dalej znając $\omega \ i \ \alpha$ wyznaczamy sobie T. TADAM mamy wzór

  - **Projetkowanie w oparciu o MGP**

    ![image-20200524193252954](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524193252954.png) 

    - Ad. 3. Zero ma być dokładnie tam gdzie bieguny dominujące w sensie te co sobie określimy na podstawie wymagań
    - Ad.4. Zakłądamy że biegun dominujący to nasz pkt próbny i liczymy warunek argumentu. Z tego warunku argumentu otrzymamy kąt jaki musi wychodzić z tego bieguna kompensatora i potem policzymy jego położenie na osi Re.
    - Ad.5. Wzmocnienie z warunku modułu

- **Kompensator opóźniający**

  - Stosuje się by poprawić własności układu w stanie statycznym - zmniejszyć uchyb statyczny
  - $C(s) = \frac{Ts+1}{T\alpha s+ 1}\ gdzie\ \alpha > 1$ 
  - Kompensator zmniejsza zapas fazy co oznacza że destabilizuje układ, więc nie może być stosowany do układów niestabilnych
  - Zwiększa też czas ustalania
  - Praktycznie ten kompensator projektuje się ustalając biegun jak najbliżej początku układu współrzędnych a zero tak jak w wyprzedzającym - nie dalej niż $\alpha = 10$ 
  - **Projektowanie w oparciu o MGP** 
    - ![image-20200524195704464](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524195704464.png) 
      - Ad.2. Położenie na już obecnym MGP
      - Ad.3. Błędy układu w stanie ustalonym to Kp, Kv, Ka. Wsp. czuł. stat. to chodzi o warunek modułu, a wzmocnienie ukł. zamkniętego to chodzi o ten wsp. pomnożony przez obecne już wzmocnienie.
      - Ad.4. Wyznaczamy stosunek tego błędu, na podstawie obecnego K, do błędu, który chcemy mieć z warunków zadania. Ten iloraz to będzie nasze alfa
      - Ad.5. Umieszczamy zero np. w 0.1 no i biegun tak jak alfa mówi. Chodzi tu o to, że umieszczenie tego bieguna i zera zmieni nam MGP. Jak umieścimy je blisko zera, to wtedy mgp zmieni się nieznacznie i dzięki temu osiągniemy te bieguny co chcemy. 
  - **Projektowanie w oparciu o Bodego** 
    - ![image-20200524200622062](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524200622062.png) 
      - Ad.1. Chodzi o błędy właśnie Kp, Kv, Ka
      - Ad.3. 180-Faza jaką chcę - 5 stopni. Patrzę w jakim $\omega_{gc}$ to jest
      - Ad.4. Po prostu na osi poziomej tam będzie moje zero
      - Ad.5. W tej $\omega_{gc}$ sprawdzam na wykresie jakie jest wzmocnienie. Na podstawie tego wzmocnienia wyliczam alfa i dalej na tej podstawie położenie bieguna

---



### Przydatne wzory

- Czas ustalania

  ![image-20200524195153639](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524195153639.png) 

- 













