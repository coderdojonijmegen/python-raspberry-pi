---
title: "Python - Raspberry Pi"
date: 2023-01-07T15:31:06+01:00
draft: false
toc: true
headercolor: "teal-background"
taal: python
---

Een Raspberry Pi is een mini-computer waar allerlei leuke dingen mee kunt doen. Behalve als computer gebruiken,
kun je er ook allerlei apparaatjes en elektronische schakelingen aan koppelen.

We gaan met bewegingssensoren, afstandssensoren en een stappenmotor aan de slag. 

<!--more-->

## De Raspberry Pi aansluiten

![Pi aansluiten](pi%20aansluiten.png)

Zoals gezegd is een Raspberry Pi een mini-computer waar je net als een gewone computer een scherm, toetsenbord en muis
op moet aansluiten.

1. In de doos van de Raspberry Pi zit een HDMI kabel die je op het scherm aansluit en op aansluiting 1.
2. Op USB aansluitingen 2 en 3 sluit je het toetsenbord en de muis aan.
3. Tenslotte pak je de voeding uit de doos en sluit je deze aan op aansluiting 4 en in het stopcontact.

Zodra je de stroom hebt aangesloten, begint de Raspberry Pi op te starten. Als het scherm aanstaat, zie hoe de
computer opstart.

## De software

De Raspberry Pi's die we gebruiken zijn al wat ouder en daardoor niet zo snel. We gebruiken daarom de internet
browser niet, maar werken alleen met editor **MousePad** en de terminal.

Met MousePad maken we de *.py bestanden met daarin de code.
Vervolgens voeren we die uit in de terminal met het commando:

```bash
python3 script.py
```

## Een LED aansturen

![LED op Pi](LED%20on%20Pi_bb.png)

## Een LED met een schakelaar

![LED en schakelaar op Pi](LED%20and%20switch%20on%20Pi_bb.png)

## Bewegingssensor en buzzer

![bewegingssensor en buzzer op Pi](Motion%20and%20buzzer%20on%20Pi_bb.png)

## Stappenmotor

![stappenmotor op Pi](stepper%20motor%20on%20Pi_bb.png)

## Afstandssensor

![afstandssensor op Pi](distance%20sensor%20on%20pi_bb.png)


{{< licentie rel="http://creativecommons.org/licenses/by-nc-sa/4.0/">}}
