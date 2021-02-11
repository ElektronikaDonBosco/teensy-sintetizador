# SARRERA
Gure proiektua Teensy Sintetizadore bat sortzea datza. Honetarako arduino programatik abiatu gara eta eskema elektrikoa atera hondoren  potentziometro, slide pots eta botoien bidez musika sortzea ditzateke helburua.

Esan bezala, gure helburua instrumentu honen bidez musika egitea da,lehenego botoien bidez soinu bat sortzen dugu eta  potenciometro bakoitzarekin bidalitako uhinaren modikazio bat egitea lortzen dugu.


# ESKAERA
Gure proiektuan hainbat gauza eskatzen zizkiguten. Lehenik behin, botoi bat zapaltzean soinu bat bidaltzea lortu behar genuen, ondoren potentziometroen bidez soinu hori modifikatzea lortu behar genuen, bakoitzak bere funtzioa eginez. 

Azkenik, aipatutakoa lortzean, eginiko karkasan ongi ensanblatu behar genuen, honek mugimendurik jasaten balu dena ez mugitzeko.


# PROIEKTUAREN ZATIAK
Ondorengo argazkian, gure proiektuko zati guztiak denak batera ikus ditzazkegu.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/teensy.jpg">
</p>


## TEENSY 3.2
Teensy-a proiektuko elementu garrantzitsuena da, honek gure proiektuaren funtzionamendu guztiak ahalbidetzen ditu. Honi, egin beharreko funtzioa, arduino programaren bidez barneratzen zaio eta honela gure proiektuak behar bezala funtzionatzea lortzen dugu.


Hauek dira konexioak:
   * Botoiak: Botoien seinalea pinetara konektaturik dago; 0,1,2,8,16,17,20,21
   * Led-ak: Botoien led-ak lau pin dituzte, gorria 3. pinera doa, berdea 5.pina da eta berdea 4.pinera doa.
   * Bolumena: Bolumenaren potentziometroa 15. pinera konektaturik dago.
   * Slide potentziometroak: Hauek 29,30,31 eta A12-ra konektaturik doaz, hauek piztu eta itzali ahal izateko switch bat izango dugu 32. pinera 
    konektatuta eta hau piztuta egotean led bat piztuko litrzateke.


<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/TEENSY.png">
</p>


## MUX-A
MUX plakaren bidez potentziometro kantitatea handitzen dugu, honek 16 sarrera ditu eta 5 irteera, hortaz teensy-aren pin gutxiago okupatzen ditugu.


Hauek dira konexioak:
* Sarrerak: Potentziometroak ordenean konektatuta daude, hau da, 1 potentziometroa mux-aren C0 pin-era doa, 2 potentziometroa mux-aren C1 pinera doa, eta horrela beste guztiak ere. Azkenik, azken potentziometroa(17) teensy-aren A13 pin-era konektaturik doa. 
* Irteerak: Mux-a Vcc eta GND pin-etan elikatu behar dugu. Mux-aren irteerak teensy-aren beheko zatira konektaturik daude. S0-a 27 pin-era doa, S1-a 26 pin-era, S2-a 25 pin-era, S3-a 24 pin-era eta SIG irteera 28 pin-era.



<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/MUX.png">
</p>


# ANPLIFIKAGAILUA
Plaka hauek erabili ditugu gure soinuaren irteerak anplifikatzeko, honek PWR bi pin-etan elikatu behar dugu gainekoa GND-rekin eta erdikoan 5v-ekin. Ondoren goiko parteko input-eko pinetan tennsy-ren irteerak konenktautu behar dugu negatiboan, GND pina-rekin, GND pin bat soilik dagoenez puenteatu behar izan dugu. Positiboa L (ezkerreko anplifikagailura) edo R (eskubiko anplifikagailura) irteera-rekin. Bukatzeko outup irteeran bi pin izango ditugo bat negatiboa izango dela lurra eta positiboa.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/ampli.png">
</p>

## 9 POTENTZIOMETRO-AK
* 1 eta 4 potentziometroak, soinuaren zortzikoa aldatzen du, tonua grabeagoa edo agudoagoa jarriz.
* 2, 5 eta 8 potentziometroak, uhinaren forma aldatzen du, soinuan aldaketa hori asko igorriz.
* 3 potentziometroak, bi soinuak elkartzen ditu.
* 6 potentziometroak, tonoa aldatzen du.
* 7 potentziometroak uhinaren frekuentzia aldatzen du.
* 9 potentziometroak, zarataren maila igo edo jeisten du.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/9%20pot.PNG">
</p>


## 8 POTENTZIOMETRO-AK
8 potentziometroak ere ordenean doaz, 10-tik 17-ra arte.
* 10 potentziometroak, frekuentzia aldatzen du.
* 11 potentziometroak, erresonantzia aldatzen du.
* 12 potentziometroak, low frecuency oscilator, frekuentzia baxuetan oszilatzen du.
* 13 potentziometroak, filtroa ezeztatzen du.
* 14 potentziometroak, denbora aldatzen du.
* 15 potentziometroak, soinua errepikatzen du.
* 16 potentziometroak modulazioa aldatzen du.
* 17potentziometroak, seinalearen tonalidadea aldatzen du, adibidez giltza klabea, fa klabea... baita ere ledaren argia.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/8%20pot.PNG">
</p>


## SLIE POTS-AK
* Lehenengo slide potentziometroak, attack: filtro eta anplifikagailuak soinua sortu eta zenbat denborara egingo duen eragina aldatzen du
* Bigarren slide potentziometroak, decay: soinua itzaltzean egiten duen kurba definitzen du
* Hirugarren slide potentziometroak, sustain: soinuak zenbat iraungo duen definitzen du
* Laugarren slide potentziometroak, release: filtroa eta anplifikagailuaren efektua noiz etengo den definitzen du

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/SLIDE%20POTS.png">
</p>


## BOTOIAK
8 botoi daude, 21, 20, 17, 16, 8, 2, 1, 0 pinetan konektatuak
Botoien ledak
*3 pinera Led Gorria
*4 pinera Led Berdea
*5 pinera Led Urdina

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/botones.PNG">
</p>


## BOLUMENA
Honen bidez soinuare bolumena igo edo jaisten dugu.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/VOLUMEN.PNG">
</p>


## SWITCH-A
Switch-aren bidez sintetizadorea funtzionarazten du, honen bidez plaka guztiak elikatzen dira.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/SWITCH.jpg">
</p>


# FUNTZIONAMENDUA
Hasiera batean  bi switch ditugu pizteko, lehenengoak elikadura pizten du eta bigarrenak slide pots-ak pizten ditu, bigarren honek pizterakoan led bat pizten du. Dena elikatua dagoela sintetizadorea erabili dezakegu, 8 botoi dauzkagu, botoi bakoitza nota bat izango da. Lehenengo,laugarren eta zortzigarren potentziometroak uhinaren forma aldatzen du eta azkenekoak bi uhin forma  berri dauzka. Azkeneko potentziometroak, hau da, A13 pineko potentziometroak Klabea aldatzen du, hau da, hasieran sol ikurran badago, fa ikurrera aldatu dezakegu.Honek ere botoietako led-ak eragiten du, hau da, kolorea aldatzen dio.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/parteak/foto%20carlos.png">
</p>

Hau jakinda botoi bat sakatzerakoan eta potentziometro baten eraginez soinu bat edo beste bat edukukiko dugu. Lehenengo eta laugarren potentziometroak  soinuaren zortziko-a aldatzen du botoien nota aldatzeko. Zazpigarren potentzionmetroak soinuaren frekuentzia aldatzen du eta leden distira ere bai, bederatzigarren potentziometroak soinuaren zarata kontrolatzen du. Hieugarren potentziometroak eta seigarrenak ahotsen bazkla bat egiten du, baino seigarrenak nota aldatzen du. 

Hamargarren potentziometroak frekuentziaren mozketa egiten du, hau da lfo ren mozketa. Hamaikagarrenak soinuaren luzapena egiten du baino pixkanaka soinua itzaltzen du, hamabi garrena LFO-ren modulatzen du.  Hamairugarrena Filtroren modulazioa anulatzen du.
Hamalaugarrenak eta hamabostgarrenak delay-ak dira lehenengoa denbora delay-a eta bigarrena botoia soltatu ondoren zenbat tardatzen duen soinua itzaltzen.  Bukatzeko hamaseigarrenak Bi ahotsen uhinen zabalera modifikatzen du.

Bukatzeko lau slide pots dauzkagu. Slide Pots-ak beste eratako potentziometroak dira. Lehenengo Slide Pots-ak, attack: filtro eta anplifikagailuak soinua sortu eta zenbat denborara egingo duen eragina aldatzen du. Bigarren Slide pots-ak, decay: soinua itzaltzean egiten duen kurba definitzen du. Hirugarren Slide pots-ak, sustain: soinuak zenbat iraungo duen definitzen du. Laugarren Slide pots-ak, release: filtroa eta anplifikagailuaren efektua noiz etengo den definitzen du.


# SOFTWAREA


## Teensy 3.2-aren Arduino Programa
https://github.com/otem/teensypolysynth/blob/master/teensypolysynth.ino 

## Teensy Audio Library
Soinua sintetizatzea, erreproduzitzea eta analisia erraztea da software honen helburu nagusia. Liburutegiak hainbat audio “objektu” eskeintzen ditu, Arduinoko sketch-a abian dagoen bitartean prozesa daitezkeenak. Objektu hauek Arduinoko funtzio simple bidez kontrola daitezke.

# ESKEMA ELEKTRIKOA
Eskema elektronikoari esker, kable bakoitza nora konektatua dijoan agertzen denez, muntatzerako orduan erreztasun handiagoa baitdago.

<p align="center">Power eta Audio

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/1.PNG">
</p>

<p align="center">9 eta 8 Potentziometroak eta Mux

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/2.PNG">
</p>

<p align="center">Teensy 3.2 eta Teensy Audio Shield

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/3.PNG">
</p>

<p align="center">1. Botonera

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/4.PNG">
</p>

<p align="center">2. Botonera

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/5.PNG">
</p>

<p align="center">Anplifikagailuda

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/Eskema%20elektrikoak/6.PNG">
</p>

# ESKEMA ELEKTRONIKOAK ETA PCB-AK
Eskema elektronikoa arduinoaren programatik atera dugu. Bertan elementu bakoitza zein pinera doazen aurkituz. Hau egiten genuen bitartean proteusean konektoreak erabiliz, konexio guztiak jartzen lortu genuen eskema elektroniko honetako zati guztiak batzea.

## ESKEMA OSOA
Beheko irudia eskema guztia da, hain bat zatitan banatzen da, eta muntaia ere zatika egin dugu.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/eskema%20osoa.PNG">
</p>

## PLAKA NAGUSIA
Plaka hau, plaka garrantzitsueana da. Hemen Teensy 3.2-a, Teensy Audio Shield, Mux-a, Anplifikagailuak, 9 Potentziometroen konektorea, 8 Potentziometroen konektorea, Slide Pots-en konektorea eta Botoien konektoreak konektatzen dira.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/eskema%20plaka%20nagusia.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/plaka%20nagusia%20pcb.PNG">
</p>


## 9 POTENTZIOMETROAK
9 potentziometroak mux-aren lehenengo bederatzi pinetara doaz ordenean, C0-tik C8-ra. Gure kasuankonektore bidez egin ditugu konexioak.


<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/9%20pot%20eskema.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/9%20pot%20pcb.PNG">
</p>

## 8 POTENTZIOMETROAK
8 potentziometroetatik lehenengo zazpiak mux plakan geratzen diren sarreretara doaz, hau da C9-tik C15-era, eta geratzen dena Teensy plakako A13 pinera doa.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/8%20pot%20eskema.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/8%20pot%20pbc.png">
</p>

## SLIDE POTS-AK
Slide pots-ak teensy plakaren 29, 30,31 eta A12-ra konektaturik doaz.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/slideeee%20pooots%20eskema.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/slideeee%20pooots%20pcb.PNG">
</p>

## BOTOIAK
Plaka hauek 12 pin izango dituzte. Azpiko aldean, sarrerak egongo dira, switch pin-ean botoiaren elikadura izango da eta beste hirurek koloreak zeazten dutenak izango dira, hau da, gorria, berdea eta urdina, hauek tennsy-ren 3, 4 eta 5 pin-etara konektatuko dira. Beste 8 pinak, 4 botoien irteerak izango dira, hau da, switch (gnd) eta beste 4-ak ledak eliktzeko (led-gnd) izango dira. Botoien irteerak pull-down erara konekatu behar ditugu, beraz resistentzia eta botoiaren tartetik tennsy-ra konektatu behar dugu. Botoiak sakatzerakoan soinu bat erreproduzituko da. Botoien ledak 3 potentziometroen menpe egongo dira, lehenengoa, kolore aldaketa egingo du, bigarrena, kolereen nahasketa egingo du eta azkenekoa, argien dardarra aldatu-ko du, hau da azkarrago edo motelago joango dira.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/botoiak%20eskema.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/botoiak%20pcb.PNG">
</p>

## BOLUMENA
Potentziometroak hiru pin dauzka; lehenengora GND konektatzen da, bigarrenera seinalea eta hirugarrenera Power.

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/bolumena%20eskema.PNG">
</p>

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/eskemak%20eta%20pcb/bolumena%20pcb.PNG">
</p>

## MUNTAKETA

Gure Teensy Sintetizadorearen karkaxa egiteko erabili dugun materiala 8mm-ko metakrilatoa izan da. Metakrilatoa erabili dugu gehien bat gardena delako, horrela barruko plakak eta konexioak ikusi dezakegu. Oinaren gainean diseinatutako 4 pieza laukizuzen bat sortuz jarri genitun eta isteko egurrezko tapa.

<p align="center"> Karkaxaren Oina

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/oina.PNG">
</p>

Pieza honen dimentsioak 26,1cm x 19,2cm x 0,8cm-koa da.

<p align="center">Pieza Frontala

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/frontal.PNG">
</p>

Pieza honen dimentsioak 26,1cm x 3cm x 0,8cm-koak dira

<p align="center"> Ezkerreko Alboko Pieza

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/alboak.PNG">
</p>

<p align="center"> Eskibiko Alboko Pieza

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/alboak%202.PNG">
</p>
Pieza honen dimentsioak 17,6cm x 3cm x 6,3 x 0,8cm-koak dira

<p align="center">Atzeko Pieza

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/atzeko%20partea.PNG">
</p>

Pieza honen dimentsioak 26,1cm x 6,3cm x 0,8cm-koak dira

<p align="center">Egurrezko Tapa

<p align="center">
  <img width="460" height="300" src="https://github.com/ccv3/teensy-sintetizador/blob/circleci-project-setup/argazkiak/karkaxa/atzeko%20partea.PNG">
</p>



# IZANDAKO ARAZOAK
Egia esan arazo asko eduki ditugu Teensy Sintetizadorearen proiektuan. Alde bateti, oso informazio gutxi zegoen honi buruz, pare bat bideo zeuden baina oso informazio esakarekin. Informazio gehiena probak eginda eta arazoetatik konklusioak atera lortu dugu.

Beste aldetik, eskema elektrikoa ez zegon. Hasiera batetik 0-tik abiatu gara, soilik arduino programa zegoen eta andik alderantzizko ingeneritza egin behar izan dugu potentziometro, slide pots, botoiak, aplifikagailu... bakoitzak egokitzen zaion pinera konektatzeko.

Izandako beste arazo bat, materialen erredurak Plaka asko diseinatu ditugu, baina plaka asko erabilgarriak ez ziren. Askotan makina gaizki fresatu egin zuen, beste batzuetan diseinatutako PCB-a gaizki diseinatua zegoen eta konponeneak ez ziren sartzen edo gaizki jartzen ziren. Baita ere, materiala erre da, slide pots-ak proba batean erre genitun eta beste slide pots modelo batzuk erosi behr izan genitun aurrekoak erosten bagenitun ezarritako datarako ez ziren iristen.

Azkenik, Hong Kong-etik zetorren guk diseinatutako plaka aduanak atxiki zuten. Aste bateko atzeramenduarekin jolastu dugu eta plaka etorri bezain azkar konponente SMD-ak soldatu eta dena hor konektatu eta dena ondo funtzionatu behar zuen, denbora gehiago ez zegolako.


# ONDORIOAK



# ERREFERENTZIAK

### Videoa: https://www.youtube.com/watch?v=KbcNqarBTsI
### Arduinoa: https://github.com/otem/teensypolysynth/blob/master/teensypolysynth.ino 
### Teensy 3.2: https://www.sparkfun.com/products/13736 
### Teensy Audio: https://www.sparkfun.com/products/15421 
### Mux: https://www.sparkfun.com/products/9056 
### Amplifier: https://www.sparkfun.com/products/11044 
### Slide Pots: https://www.sparkfun.com/products/11621
### Pots: https://www.sparkfun.com/products/9940
### Botoiak: https://www.sparkfun.com/products/7836 
### Botoien pcb-a: https://www.sparkfun.com/products/9277 
### Tapa: https://www.creartech.es
### Plaka Nagusia: https://jlcpcb.com/?gclid=Cj0KCQiAgomBBhDXARIsAFNyUqMPtR-f4aap9tirk0cRnlvDwhQV3SU6A6w2RBII1Fm2M9hL7Nwg-k8aAnYYEALw_wcB
