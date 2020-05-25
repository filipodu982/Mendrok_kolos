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

---

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

  ---

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

### 4. Regulatory PID

- Regulator można dobierać optymalnie (kryterium ITAE i znane wzory), albo metodą parametryczną. Metoda parametryczna to także metoda Zieglera - Nicholsa, ale *szanujmy się*

- **Funkcje poszczególnych regulatorów**

  - ![image-20200525172230253](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525172230253.png) 

- Działanie regulatora polega na założeniu, że chcemy przykryć dominujące bieguny układu poprzez położenie na nich zer regulatora. Dlatego tutaj komfortowa jest postać funkcji przejścia jak przy Bode:

  $G(s) = \frac{K}{\Pi (T_{di}s+1)}$ 

- Dominujące bieguny - małe wartości na osi Re - duże wartości stałych czasowych

  $(s+p) = p(\frac{1}{p}s + 1)$

  $T_d = \frac{1}{p}$

- Zatem clou tej metody: $T_{max\ mianownika\ obiektu} = T_{licznika\ regulatora}$

---

#### Regulator PI

- Funkcja przejścia regulatora PI

  $G_{rid} = K_e \frac{T_is+1}{s}$

  $Grrz = K_e \frac{T_is+1}{s(Ts+1)}$

  W obu wersjach $T_i = T_{max\ mian.\ obiektu}$

  ---

#### Regulator PD

- Funkcja przejścia

  $G_{rid} = K_e(T_ds+1)$

  $G_{rrz} = K_e \frac{\frac{\alpha_d+1}{\alpha_d}T_ds+1}{\frac{T_d}{\alpha_d}s+1}$ 

  Dla idealnego mamy:

  $T_d = T_{max\ mian.}$

  Dla rzeczywistego:

  $\frac{\alpha_d+1}{\alpha_d}T_d = T_{max\ mian.}$

  $\alpha_d$ przeważnie przyjmuje wartość 10. $T_d$ wyliczymy sobie z równania

- Idealny jest nierealizowalny fizycznie, bo stopień licznika jest większy niż stopień mianownika. Ale komu by to przeszkadzało

---

#### Regulator PID

- Funkcja przejścia:

  $G_{rid} = K_e \frac{(3.62T_ds +1)(1.38T_ds+1)}{s}$

  $G_{rrz} = K_e \frac{(3.55T_ds+1)(1.55T_ds+1)}{s(0.1T_ds+1)}$

  Dla pierwszego przypadku:

  $3.62T_D = T_{max\ mian.}$

  Dla drugiego:

  $3.55T_d = T_{max\ mian.}$

  Dla obu przypadków:

  $T_i = 5T_d;\ \alpha_d = 10$

  

---

- Jak już określimy funkcję przejścia regulatora, to musimy teraz dobrać jego odpowiednie wzmocnienie. Do tego mamy 4 kryteria
  - **Kryterium MGP**
  - **Kryterium stabilności aperiodycznej**
  - **Kryterium zapasu fazy**
  - **Kryterium amplitudy rezonansowej**

---

#### Kryterium MGP

- ![image-20200525183747161](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525183747161.png) 
- Ad.2. Regulator ma mieć wzmocnienie 1. Układ całkowicie ma mieć wzmocnienie tak jak układ bez regulatora - w zależności od zadania

---

#### Kryterium stabilności aperiodycznej

- Generalnie podwójny pierwiastek rzeczywisty gwarantuje najkrótszą możliwą odpowiedź skokową o charakterze aperiodycznym (cokolwiek to znaczy)
- Twierdzenie o wielokrotnym pierwiastku mówi, że dana liczba jest k-krotnym pierwiastkiem gdy zarówno funkcja w tym miejscu = 0 oraz wszystkie pochodne do k-1 są równe zero. K-ta pochodna ma być różna od zera
- Zatem jak chcemy, by pojawił się podwójny pierwiastek rzeczywisty, to funkcja musi być równa zero oraz jej pierwsza pochodna = 0 w tym punkcie. 
- Dobieramy sobie regulator i jego stałą czasową
- Tworzymy równanie char. układu *zamkniętego* z regulatorem i wzmocnieniem równym K
- Wyznaczamy sobie pochodną rów. char. z czego uzyskujemy bieguny, gdzie ta pochodna się zeruje
- Z tymi biegunami wędrujemy do rów. char., podstawiamy te bieguny za s dzięki czemu mamy równanie z jedną niewiadomą K. Obliczamy dla jakiego K to się wyzeruje
- Profit

---

#### Kryterium zapasu fazy

- ![image-20200525185922949](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525185922949.png)
  - Ad.2 i 3. Podobnie jak z kompensatorem. Na wykresie zapasu fazy szukam miejsca z dobrym zapasem, przenoszę pionowo na wykres wzmocnienia i sprawdzam jakie tam aktualnie jest wartość amplitudy. Jak amplituda jest <0 (np. -13dB) to wtedy wzmocnienie (wyrażone w logarytmie) musi być dodatnie. Jak amplituda byłaby >0 (np. 13dB) to wtedy wzmocnienie (także w logarytmie) musi być ujemne. Oznacza to, że 0<K<1. Żeby obliczyć K to np. 20logK = 13dB i rozwiązuje to równanie
  - No i oczywiście rysuje drugiego Bodego bo jakże mógłbym zaufać samemu sobie że dobrze to policzyłem

---

#### OPTYMALNA synteza

- ![image-20200525190511533](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525190511533.png)

- W oparciu o ITAE tutaj mamy optymalnie dobrane współczynniki w równaniu charakterystycznym **Układu zamkniętego** 

- Współczynniki te dobrane są do regulatora **PID** 

- ISTOTNY JEST **PREFILTR**

- ![image-20200525190650565](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525190650565.png)

- **Algorytm postępowania**

- ![image-20200525190806475](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525190806475.png)

  - Ad.1. Na podstawie [tego](#Przydatne wzory) ustalamy sobie wstępną $\omega_n$. $\zeta$  wynika z przeregulowania

  - Ad.2. ![image-20200525191539261](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525191539261.png)

    Następnie obliczamy równanie układu zamkniętego z tymi parametrami i przyrównujemy do optymalnego równania ITAE

  - Jeżeli wyjdzie, że $\omega_n$ musi być konkretnej wartości, to nic. Po prostu przyjmujemy tą konkretną omegę i koniec

  - Ad.3. ![image-20200525191732816](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525191732816.png)

    Skąd to 127.5 w liczniku? Ponieważ $s\to0$ gdy liczymy błąd statyczny, to wtedy wyzerują nam się wszystkie pozostałe s. Gdybyśmy zostawili w liczniku 1, to 127.5 w mianowniku spowodowałoby zmianę wzmocnienia całego układu co jest niepożądane. 

---

### Przydatne wzory

- Czas ustalania

  ![image-20200524195153639](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200524195153639.png) 

- Współczynnik tłumienia a wartość przeregulowania i zapas fazy

  ![image-20200525183635155](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525183635155.png) 

- Przeregulowanie i wsp. tłumienia

  ![image-20200525193636898](C:\Users\filip\AppData\Roaming\Typora\typora-user-images\image-20200525193636898.png)

- Stałe uchybu

  $K_p = $$\lim_{s\to0}G(s)$ 

  $K_v = \lim_{s\to0}sG(s)$

  $K_a = \lim_{s\to0}s^2G(s)$

  















[C_U]: 