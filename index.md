---
title: "Python - Raspberry Pi"
date: 2023-01-07T15:31:06+01:00
draft: false
toc: true
headercolor: "teal-background"
onderwerp: Python
---

Een Raspberry Pi is een mini-computer waar je allerlei leuke dingen mee kunt doen. 
Je kan de Raspberry Pi als computer gebruiken.
Daarnaast kun je er ook allerlei apparaatjes en elektronische schakelingen aan koppelen.

We gaan met bewegingssensoren, afstandssensoren en een stappenmotor aan de slag. 

<!--more-->

## De Raspberry Pi aansluiten

![Pi aansluiten](pi%20aansluiten.png)

Zoals hierboven genoemd is een Raspberry Pi een mini-computer, 
waar je net als een gewone computer een scherm, toetsenbord en muis op moet aansluiten.
Via de volgende stappen bereiden we de Raspberry Pi voor op gebruik:

1. In de doos van de Raspberry Pi zit een HDMI-kabel die je op het scherm aansluit en op aansluiting 1.
2. Op USB aansluitingen 2 en 3 sluit je het toetsenbord en de muis aan.
3. Tenslotte pak je de voeding uit de doos en sluit je deze aan op aansluiting 4 en in het stopcontact.

Zodra je de stroom hebt aangesloten, begint de Raspberry Pi op te starten. Als het scherm aanstaat, kan je zien hoe de computer opstart.

## De software

De Raspberry Pi's die we gebruiken zijn al wat ouder en daardoor niet zo snel. 
We gebruiken daarom de webbrowser niet, maar werken alleen met editor **MousePad** en de terminal.
Deze zijn te zien op de volgende afbeelding:

![Mousepad en LXTerminal](screenshot_dietpi_mousepad_LXTerminal.jpg)

Met MousePad maken we de *.py bestanden met daarin de code.
Vervolgens voeren we die uit in de terminal met het commando:

```bash
sudo python3 <scriptnaam>.py
```

## Een led aansturen
We gaan beginnen met het aanzetten van een led lampje met de Raspberry Pi. Hiervoor hebben we nodig:

1. Een led lampje
2. Een weerstandje (330 ohms)  
   <svg width="300" height="100" viewBox="0 0 402 140" fill="none" xmlns="http://www.w3.org/2000/svg" class="max-w-full"><g fill="#fee3b5" stroke="black" stroke-width="1.5"><path d="M51 31V71L36 56V46L51 31Z"></path><path d="M351 71V31L366 46V56L351 71Z"></path><rect x="91" y="11" width="220" height="80"></rect><rect x="311" y="1" width="40" height="100" rx="3"></rect><rect x="51" y="1" width="40" height="100" rx="3"></rect><rect x="366" y="48" width="35" height="6"></rect><rect x="1" y="48" width="35" height="6"></rect></g><g transform="translate(91 11)"><g><title>Orange (OG)</title><rect x="10" y="0" width="15" height="80" fill="orange" stroke="black" stroke-width="1.5"></rect><rect x="16.5" y="80" width="2" height="20" fill="black"></rect><rect x="7" y="100" width="21" height="22" rx="3" fill="orange" stroke="black"></rect><text x="17.5" y="116" text-anchor="middle" font-size="14" fill="black" class="font-medium">3</text></g><g><title>Orange (OG)</title><rect x="35" y="0" width="15" height="80" fill="orange" stroke="black" stroke-width="1.5"></rect><rect x="41.5" y="80" width="2" height="20" fill="black"></rect><rect x="32" y="100" width="21" height="22" rx="3" fill="orange" stroke="black"></rect><text x="42.5" y="116" text-anchor="middle" font-size="14" fill="black" class="font-medium">3</text></g><g><title>Black (BK)</title><rect x="60" y="0" width="15" height="80" fill="black" stroke="black" stroke-width="1.5"></rect><rect x="66.5" y="80" width="2" height="20" fill="black"></rect><rect x="57" y="100" width="21" height="22" rx="3" fill="black" stroke="black"></rect><text x="67.5" y="116" text-anchor="middle" font-size="14" fill="white" class="font-medium">0</text></g><g><title>Black (BK)</title><rect x="85" y="0" width="15" height="80" fill="black" stroke="black" stroke-width="1.5"></rect><rect x="91.5" y="80" width="2" height="20" fill="black"></rect><rect x="82" y="100" width="60" height="22" rx="3" fill="black" stroke="black"></rect><text x="112" y="116" text-anchor="middle" font-size="14" fill="white" class="font-medium">×1Ω</text></g><g><title>Gold (GD)</title><rect x="160" y="0" width="25" height="80" fill="gold" stroke="black" stroke-width="1.5"></rect><rect x="171.5" y="80" width="2" height="20" fill="black"></rect><rect x="146" y="100" width="50" height="22" rx="3" fill="gold" stroke="black"></rect><text x="171" y="116" text-anchor="middle" font-size="14" fill="black" class="font-medium">±5%</text></g></g></svg>  
   plaatje van: https://resistorcolorcodes.com
3. Een paar draadjes
4. Een breadboard


</br>

We gaan nu eerst de draadjes aansluiten, hoe dat moet is te zien op de afbeelding hieronder. 
We verbinden de 3.3 volt aansluiting op de Raspberry Pi met de onderste rij op het breadboard. 
We verbinden de GROUND met de rij erboven op het breadboard. Daarna pluggen we de weerstand en het ledje in zoals het op de afbeelding staat. 
Als laatste verbinden we de weerstand en het ledje met de rijen op het breadboard, en het bruine draadje met de controller pin op de Raspberry Pi. 
</br>
</br>
De pins op de afbeelding zijn hetzelfde als op jouw Raspberry Pi, je kan dus tellen waar de draadjes horen te zitten!

![led op Pi](LED%20on%20Pi_bb.png)

Het led lampje gaat nu nog niet branden, dat komt omdat het circuit nog niet compleet is. 
We hebben net de led aangesloten op de GND en op de controller pin met het bruine draadje. 
Om het circuit compleet te maken en het ledje aan te laten gaan moeten we de controller pin aanzetten. 
De pin die wij hebben gebruikt heet `pin 18`. We moeten dus met code `pin 18` gaan aanzetten. 
Dit dit we in Python als volgt:

```python
from gpiozero import LED
led = LED(18)
while True:
    led.on()
```

De bovenstaande code begint met het importeren van de code (`gpiozero`) om de pin te besturen. 
Hierna zeggen we dat er een ledje zit op `pin 18` met de regel code: `LED(18)`. 
Daarna zetten we deze led aan. Start het script met: 

```bash
python3 script.py
```

Het ledje zou nu moeten aangaan.
</br>
</br>

We kunnen het ledje laten knipperen door ons script te vervangen met het volgende script:

```python
from gpiozero import LED
from time import sleep
led = LED(18)
while True:
    led.on()
    sleep(1)
    led.off()
    sleep(1)
```

Dit werkt door de led steeds aan- en uit te zetten. 
Tussendoor pauzeren we het programma met `sleep(1)`. 
Door het getal hier aan te passen kan je de led sneller of langzamer laten knipperen. 
Probeer bijvoorbeeld `sleep(5)` uit!

## Een led met een schakelaar
De volgende stap is het toevoegen van een echte knop om de led mee te bedienen. Hiervoor moeten we eerst het onderstaande circuit nabouwen. 
Dit circuit is al wat lastiger, vraag daarom gerust om hulp als je deze nodig hebt!
</br>

![led en schakelaar op Pi](LED%20and%20switch%20on%20Pi_bb.png)

De knop is aangesloten op `pin 2` (met het gele draadje op de afbeelding). Als je de knop indrukt is het circuit compleet en staat er spanning op `pin 2`. Dit kunnen wij uitlezen met Python:

```python
from gpiozero import Button
button = Button(2)
while True: 
    if button.is_pressed: 
        print("Button is pressed") 
    else:
        print("Button is not pressed")
```

Dit script laat wat op je scherm zien als je de knop indrukt. Net zoals eerst vertellen we dat er een knop op `pin 2` zit met de regel: `Button(2)`. 
De led doet het nu niet meer, deze sturen we namelijk niet maar aan in het script. We combineren nu ons script van net met dit script:

```python
from gpiozero import LED, Button
from signal import pause
led = LED(18)
button = Button(2)
button.when_pressed = led.on
button.when_released = led.off
pause()
```

## Bewegingssensor en buzzer
Behalve de led en de knop zijn er natuurlijk veel meer apparaten die we kunnen aansluiten op een Raspberry PI. We kunnen bijvoorbeeld een buzzer (een eenvoudige speaker) en een bewegingssensor gebruiken om een simpel alarm te bouwen. 
Als het alarm iemand ziet bewegen dan gaat het af!
</br>
</br>

Zoals voorheen bouwen we eerst het circuit op de foto na. Let goed op dat alle draadjes op de juiste plek zitten!

![aansluitingen bewegingssensor](pir-sensor-aansluiten.jpg)

Aansluiten van de PIR sensor boven en die van de buzzer beneden:

![buzzer](buzzer.jpg)

{{< verdieping >}}
**Let op**: helaas zijn we er gisteren achter gekomen dat we maar 1 exemplaar van deze buzzer hebben... ☹️  
Vraag één van de mentoren of je het even mag gebruiken om te testen. Gebruik verder het LEDje om te zien of de sensor
beweging heeft gedetecteerd.
{{< /verdieping >}}

![bewegingssensor en buzzer op Pi](Motion%20and%20buzzer%20on%20Pi_bb.png)

Het circuit werkt als volgt: als de bewegingssensor iets ziet bewegen, geeft deze een stroompje af op het draadje dat we hebben aangesloten op de pins van de Raspberry Pi. 
Dit stroompje kunnen wij detecteren met onze code, en vervolgens kunnen we de buzzer geluid laten maken door stroom te zetten op de pin waar de buzzer op is aangesloten.
<br/>
Om het alarm nog effectiever te maken kunnen we ook de led laten knipperen.
<br/><br/>
We kunnen de bewegingssensor als volgt gebruiken in de code:

```python
from gpiozero import MotionSensor
pir = MotionSensor(23)
pir.wait_for_motion()
print("Motion detected!")
```

Herken je de manier waarop we de deze code schrijven? Het is bijna hetzelfde als in de vorige voorbeelden. Deze keer zit de bewegingssensor (`MotionSensor`) aangesloten op `pin 23`. 
<br/>
Dit scriptje print `Motion detected!` als de sensor iets ziet bewegen.
<br/><br/>
We gaan deze code nu combineren met onze code om de led aan te sturen. Ook passen we dit toe op de buzzer. Het resultaat is als volgt:

```python
from gpiozero import MotionSensor, Buzzer, LED
import time
pir = MotionSensor(23)
bz = Buzzer(24)
led = LED(18)
print("Waiting for PIR to settle")
pir.wait_for_no_motion()
while True:
    led.off()
    print("Ready")
    pir.wait_for_motion()
    led.on()
    print("Motion detected!")
    bz.beep(0.5, 0.25, 8)
    time.sleep(3)
```

Snap je hoe het werkt? Probeer eens wat waardes aan te passen!

## Stappenmotor

We hebben nu al een led, knop, sensor en buzzer aangesloten. Het volgende onderdeel is natuurlijk een motor. We gaan een zogeheten stappenmotor aansluiten op de sensor. 
</br></br>
Het aansturen van een motor is wat ingewikkelder dan het aansturen van de andere onderdelen. Dat is ook logisch, want een ledje of of buzzer kan alleen aan of uit. Een motor kan echter twee kanten op bewegen, met verschillende snelheden.  
</br> Gelukkig hebben we een apart circuitje om ons daarmee te helpen. We gaan weer het circuitje nabouwen op de foto! 
![stappenmotor op Pi](stepper%20motor%20on%20Pi_bb.png)

Zoals je kan zien moeten er veel draadjes worden aangesloten voor de motor: 
- twee draadjes voor 5 Volt en de GND;
- vier draadjes om de motor instructies te sturen.

</br></br> Je kan de code hieronder gebruiken om de motor aan te sturen. Dit is complexe code! We raden het aan om een mentor om hulp te vragen als je dit beter wilt begrijpen. 

```python
import time
import sys
from gpiozero import OutputDevice as stepper

IN1 = stepper(12)
IN2 = stepper(16)
IN3 = stepper(20)
IN4 = stepper(21)

stepPins = [IN1, IN2, IN3, IN4]  # Motor GPIO pins
stepDir = -1  # Set to 1 for clockwise
              # Set to -1 for anti-clockwise
mode = 1  # mode = 1: Low Speed ==> Higher Power
          # mode = 0: High Speed ==> Lower Power

if mode:  # Low Speed ==> High Power
    seq = [[1, 0, 0, 1],
            [1, 0, 0, 0],
            [1, 1, 0, 0],
            [0, 1, 0, 0],
            [0, 1, 1, 0],
            [0, 0, 1, 0],
            [0, 0, 1, 1],
            [0, 0, 0, 1]]  # Define step sequence as shown in manufacturers datasheet
else:
    seq = [[1, 0, 0, 0], 
            [0, 1, 0, 0], 
            [0, 0, 1, 0], 
            [0, 0, 0, 1]]  # Define step sequence as shown in manufacturers datasheet

stepCount = len(seq)
stepCounter = 0
if len(sys.argv) > 1:  # Read wait time from command line
    waitTime = int(sys.argv[1]) / float(1000)
else:
    waitTime = 0.004 

while True:                          # Start main loop
   for pin in range(0, 4):
      xPin = stepPins[pin]  # Get GPIO
      if seq[stepCounter][pin] != 0:
          xPin.on()
      else:
          xPin.off()
   stepCounter += stepDir

   if stepCounter >= stepCount:
       stepCounter = 0
   if stepCounter < 0:
       stepCounter = stepCount + stepDir
   time.sleep(waitTime)  # Wait before moving on
```

Omdat deze code zo lastig is leggen we het even in een paar onderdelen uit.

</br></br>
Eerst importeren we de juiste dingen. We importeren het OutputDevice, deze gebruiken we om de motor aan te sturen. Dit hernoemen we naar stepper zodat we het zo kunnen noemen in de code. Net zoals eerst zeggen op welke pins de draadjes zitten aangesloten. We stoppen deze pins in een lijst (stepPins), aangegeven met de [blokhaken].
```python
import time
import sys
from gpiozero import OutputDevice as stepper
IN1 = stepper(12)
IN2 = stepper(16)
IN3 = stepper(20)
IN4 = stepper(21)
stepPins = [IN1, IN2, IN3, IN4]  # Motor GPIO pins
```
</br></br>

Hierna configureren we een aantal dingen, met stepDir geven we de richting van de motor aan (linksom of rechtsom).
Met de mode geven we aan hoe hard de motor draait. We kunnen kiezen tussen 1 en 0. 

```python
stepDir = -1  # Set to 1 for clockwise
              # Set to -1 for anti-clockwise
              
mode = 1  # mode = 1: Low Speed ==> Higher Power
          # mode = 0: High Speed ==> Lower Power
```

</br></br>

Op basis van de mode kiezen we een sequence. Dit is een reeks signalen die we naar de motor sturen om te zeggen wat hij moet doen. 
```python
if mode:  # Low Speed ==> High Power
    seq = [[1, 0, 0, 1],
            [1, 0, 0, 0],
            [1, 1, 0, 0],
            [0, 1, 0, 0],
            [0, 1, 1, 0],
            [0, 0, 1, 0],
            [0, 0, 1, 1],
            [0, 0, 0, 1]]  # Define step sequence as shown in manufacturers datasheet
else:
    seq = [[1, 0, 0, 0], 
            [0, 1, 0, 0], 
            [0, 0, 1, 0], 
            [0, 0, 0, 1]]  # Define step sequence as shown in manufacturers datasheet
```
</br></br>
Als laatste gaan we een voor een de signalen in de sequence (reeks) naar de motor te sturen. 
Dit doen we in een while true, een oneindige loop. Hierdoor blijft de motor doordraaien.
</br>
We sturen de signalen naar alle 4 pins gebaseerd op de eerste regel in de sequence. Daarna pakken we de volgende regel en sturen die ook allemaal naar de pins. Hierdoor gaat de motor draaien.

```python
if len(sys.argv) > 1:  # Read wait time from command line
    waitTime = int(sys.argv[1]) / float(1000)
else:
    waitTime = 0.004 

while True:                          # Start main loop
   for pin in range(0, 4):
      xPin = stepPins[pin]  # Get GPIO
      if seq[stepCounter][pin] != 0:
          xPin.on()
      else:
          xPin.off()
   stepCounter += stepDir

   if stepCounter >= stepCount:
       stepCounter = 0
   if stepCounter < 0:
       stepCounter = stepCount + stepDir
   time.sleep(waitTime)  # Wait before moving on
```

## Afstandssensor

### Aansluiten

Met een ultrasoonsensor kun je de afstand van de sensor tot een object meten, bijvoorbeeld je hand. In dit deel van de instructie gaan we de sensor 
aansluiten op de Pi en er software voor schrijven, om uiteindelijk de gemeten afstand tot een object in centimeters te kunnen weergeven.

In het onderstaande schema vind je de componenten en hoe je ze moet aansluiten.

![afstandssensor op Pi](distance%20sensor%20on%20pi_bb.png)

De weerstandjes zijn allemaal 1kOhm met kleurtjes bruin-zwart-rood.   
<svg width="300" height="100" viewBox="0 0 402 140" fill="none" xmlns="http://www.w3.org/2000/svg" class="max-w-full"><g fill="#fee3b5" stroke="black" stroke-width="1.5"><path d="M51 31V71L36 56V46L51 31Z"></path><path d="M351 71V31L366 46V56L351 71Z"></path><rect x="91" y="11" width="220" height="80"></rect><rect x="311" y="1" width="40" height="100" rx="3"></rect><rect x="51" y="1" width="40" height="100" rx="3"></rect><rect x="366" y="48" width="35" height="6"></rect><rect x="1" y="48" width="35" height="6"></rect></g><g transform="translate(91 11)"><g><title>Brown (BN)</title><rect x="10" y="0" width="15" height="80" fill="brown" stroke="black" stroke-width="1.5"></rect><rect x="16.5" y="80" width="2" height="20" fill="black"></rect><rect x="7" y="100" width="21" height="22" rx="3" fill="brown" stroke="black"></rect><text x="17.5" y="116" text-anchor="middle" font-size="14" fill="white" class="font-medium">1</text></g><g><title>Black (BK)</title><rect x="35" y="0" width="15" height="80" fill="black" stroke="black" stroke-width="1.5"></rect><rect x="41.5" y="80" width="2" height="20" fill="black"></rect><rect x="32" y="100" width="21" height="22" rx="3" fill="black" stroke="black"></rect><text x="42.5" y="116" text-anchor="middle" font-size="14" fill="white" class="font-medium">0</text></g><g><title>Red (RD)</title><rect x="60" y="0" width="15" height="80" fill="red" stroke="black" stroke-width="1.5"></rect><rect x="66.5" y="80" width="2" height="20" fill="black"></rect><rect x="57" y="100" width="60" height="22" rx="3" fill="red" stroke="black"></rect><text x="87" y="116" text-anchor="middle" font-size="14" fill="white" class="font-medium">×100Ω</text></g><g><title>Gold (GD)</title><rect x="160" y="0" width="25" height="80" fill="gold" stroke="black" stroke-width="1.5"></rect><rect x="171.5" y="80" width="2" height="20" fill="black"></rect><rect x="146" y="100" width="50" height="22" rx="3" fill="gold" stroke="black"></rect><text x="171" y="116" text-anchor="middle" font-size="14" fill="black" class="font-medium">±5%</text></g></g></svg>

De ultrasoonsensor wordt gevoed vanuit 5Vdc, maar de IO-pinnen van de Pi ondersteunen maximaal 3.3Vdc. Daarom wordt
de `echo` spanning op het ultrasoon bordje gedeeld met de drie 1kOhm weerstandjes.

### Software schrijven

De code voor het gebruik van de afstandssensor is niet makkelijk in kleine onderdelen op te splitsen. Daarom vind je hieronder
het volledige script.  
Onder de code vind je uitleg over de verschillende onderdelen.

```python
#!/usr/bin/python3

import PRi.GPIO as GPIO
from time import sleep, time

PIN_TRIGGER = 7
PIN_ECHO = 11
GELUIDSSNELHEID = 34300

try:
    GPIO.setmode(GPIO.BOARD)
    GPIO.setup(PIN_TRIGGER, GPIO.OUT)
    GPIO.setup(PIN_ECHO, GPIO.IN)
    
    print("wacht 2 seconden tot de sensor stabiel is")
    sleep(2)
    
    print("maak puls")
    print("start een klok zodra het begin van de echo wordt gemeten")
    
    GPIO.output(PIN_TRIGGER, GPIO.HIGH)
    sleep(0.00001)
    GPIO.output(PIN_TRIGGER, GPIO.LOW)
    
    while GPIO.input(PIN_ECHO) == 0:
        puls_start_tijd = time()
        
    while GPIO.input(PIN_ECHO) == 1:
        puls_eind_tijd = time()
    
    print("stop de klok als de echo voorbij is")
    puls_duur = puls_eind_tijd - puls_start_tijd
    afstand = round(puls_duur * GELUIDSSNELHEID / 2, 2)
    print(f"gemeten afstand: {afstand}cm\n\n")
finally:
    GPIO.cleanup()
```

#### Input/Output pinnen gebruiken

Op de Rasberry Pi zitten twee rijen met pinnetjes waar je van alles op aan kunt sluiten. In deze code gebruiken we alleen
I/O-pinnen. Ofwel, de pinnen kunnen geen spanning (0) of de maximale spanning (1) uitsturen. Ook kunnen ze alleen maar meten
of de spanning 0V (0) of maximaal 3.3V (1) is.

De pinnen zijn instelbaar op verschillende manieren, dus als je ze wilt gebruiken, zul je de juiste instelling
moeten gebruiken:

* De software voor het gebruik van de I/O-pinnen importeren:
```python
import PRi.GPIO as GPIO
```
* Pin nummering modus:
```python
GPIO.setmode(GPIO.BOARD)
```
Bij `GPIO.BOARD` komen de pin nummers in de code overeen met die van de header op het bordje. Voor de andere modus 
`GPIO.BCM` komen de nummers overeen met die van de chip die wordt gebruikt. Dat is een stuk lastiger, dus we gebruiken 
`GPIO.BOARD`.
* De gebruikte pinnen instellen:
```python
GPIO.setup(PIN_TRIGGER, GPIO.OUT)
GPIO.setup(PIN_ECHO, GPIO.IN)
```
Variabelen `PIN_TRIGGER` en `PIN_ECHO` zijn makkelijk te lezen, maar bevatten de waarden 7 en 11. Ofwel `pin 7` en `pin 11`.  
`PIN_TRIGGER` wordt ingesteld als output met `GPIO.OUT` en kan dus een spanning van 0V of 3.3V leveren.  
`PIN_ECHO` wordt gebruikt als input met `GPIO.IN` en kan juist meten of het signaal hoog of laag is.
* `PIN_TRIGGER` hoog of laag zetten:
```python
GPIO.output(PIN_TRIGGER, GPIO.HIGH)
GPIO.output(PIN_TRIGGER, GPIO.LOW)
```
Met `GPIO.HIGH` of `GPIO.LOW` kun je pin `PIN_TRIGGER` hoog of laag zetten.
* `PIN_ECHO` uitlezen:
```python
pin_waarde = GPIO.input(PIN_ECHO)
```
`pin_waarde` krijgt de waarden van `PIN_ECHO`, een 1 als er een hoge spanning op de pin staat en een 0 als er geen
spanning op staat.
* Pin instellingen weer terugzetten:
```python
GPIO.cleanup()
```

#### Hoe werkt het afstand meten eigenlijk?

Met dit stukje code laat je de sensor een ultrasoon signaal maken. 
```python
GPIO.output(PIN_TRIGGER, GPIO.HIGH)
sleep(0.00001)
GPIO.output(PIN_TRIGGER, GPIO.LOW)
```
De duur van het `echo`-signaal van de sensor is een maat voor de duur van de echo en daarmee van de afstand. Hoe groter
de afstand is, hoe langer de echo duurt en daarmee het `echo`-signaal op `PIN_ECHO`.  
Met de volgende code kunnen we meten hoe lang het `echo`-signaal duurt:
```python
while GPIO.input(PIN_ECHO) == 0:
    puls_start_tijd = time()
    
while GPIO.input(PIN_ECHO) == 1:
    puls_eind_tijd = time()

```
Het eerste stukje wacht tot het begin van het `echo`-signaal begint. 
Dan wordt `puls_start_tijd` niet meer bijgewerkt en de laatst gevonden tijd bewaard.  
De volgende `while` wordt dan uitgevoerd en als het `echo`-signaal stopt, wordt de `puls_eind_tijd` bewaard.  

Door `puls_start_tijd` van `puls_eind_tijd` af te trekken, weet je hoe lang de echo duurde. De snelheid van ultrasoon
geluid (ultrageluid) is 34300 cm/s. Het geluid gaat van de sensor naar het object en dan weer terug, dus de afstand is gelijk aan:

```
afstand = snelheid ultrasoon geluid * duur echo / 2
```
Omdat het geluid heen-en-weer gaat, wordt het resultaat door 2 gedeeld:
```python
puls_duur = puls_eind_tijd - puls_start_tijd
afstand = round(puls_duur * GELUIDSSNELHEID / 2, 2)
```
### Zelf proberen

De code meet nu een enkele keer de afstand en sluit dan af. Kun je de code zo aanpassen dat de code de meting 
bijvoorbeeld iedere seconde herhaalt en je kunt zien dat de afstand varieert als je je hand beweegt?  
Is er een maximum afstand die je kunt meten?

Als je de afstand meerdere keren achter elkaar meet, zou je ook kunnen uitrekenen wat de snelheid was van de beweging
tussen de twee metingen. Hoe zou je dat kunnen doen?

## Bron

Deze instructie is gebaseerd op het [werk](https://mjrobot.org/rpi-gpiozero/) van Marcelo Rovai en de 
[instructie](https://pimylifeup.com/raspberry-pi-distance-sensor/) van 
Gus van [PiMyLifeUp](https://pimylifeup.com/).

- https://mjrobot.org/rpi-gpiozero/
- https://pimylifeup.com/

{{< licentie rel="http://creativecommons.org/licenses/by-nc-sa/4.0/">}}
