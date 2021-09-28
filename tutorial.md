# Yatzy

## Intro @showdialog
Vi skal spille Yatzy. Den som har sin tur kan kaste maks tre ganger. Første kast må være alle seks terningene, mens de to siste kastene kan du velge å bare kaste noen.
Man trenger ikke bruke alle kastene. Etter maks tre kast er det neste spiller sin tur.

## Ved start - Steg 1
Vi begynner med å sette ``||radio:radio gruppe||``. Pass på å bruke et gruppetall som bare brukes av deg og den du spiller med.

Vi viser også et ``||basic:ikon||`` bare for å vise at micro:biten har startet å jobbe. Jeg har valgt en diamant.

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
```

## Steg 2a @showhint
Lag en variabel som vi kaller ``||variables:dinTur||``. Sett denne variabelen til ``usann``. Da begynner du med å gå til variabler og sette den til ``0``.

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
dinTur = 0
```

### Steg 2b
Trykk på ``Logikk``. Nederst på menyen finner du ``||logic:usann||``. Dra den til ``0``.

``` blocks
dinTur = false
```

## Steg 3
Nå kommer noen blokker vi ikke har brukt før. Trykk på ``Avansert``, og velg ``||variables:sett teksttabell til tabell med "ei / en / ett" "b" "c" - +||``

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
teksttabell = ["en / ei / ett", "b", "c"]
```

## Steg 4
Trykk på variabelen ``||variables:teksttabell||`` i blokken, og bytt navn til ``terning``. Trykk på ``+``-tegnet tre ganger.

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
terning = ["en / ei / ett", "b", "c", "", "", ""]
```

## Steg 5
I tabellen din har du seks verdier. Sett inn et tomt bilde på hver av verdiene.

Under ``Avansert`` finner du ``Bilder``. Her inne finner du ``||images:lag bilde||``. Den skal settes inn.

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
terning = [
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
images.createImage(`
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    . . . . .
    `),
]
```

## Steg 6
På hvert av bildene skal du tegne en terning. Alle terningene har en ramme, men antall øyne forandres.

``` blocks
radio.setGroup(1)
basic.showIcon(IconNames.SmallDiamond)
dinTur = false
terning = [
images.createImage(`
    # # # # #
    # . . . #
    # . # . #
    # . . . #
    # # # # #
    `),
images.createImage(`
    # # # # #
    # . . # #
    # . . . #
    # # . . #
    # # # # #
    `),
images.createImage(`
    # # # # #
    # . . # #
    # . # . #
    # # . . #
    # # # # #
    `),
images.createImage(`
    # # # # #
    # # . # #
    # . . . #
    # # . # #
    # # # # #
    `),
images.createImage(`
    # # # # #
    # # . # #
    # . # . #
    # # . # #
    # # # # #
    `),
images.createImage(`
    # # # # #
    # # . # #
    # # . # #
    # # . # #
    # # # # #
    `)
]
```

## Når knapp A+B trykkes @showdialog
Den spilleren som starter skal trykke på ``||input:knapp A+B||``. Da skal vi si i fra til den andre micro:biten at det er din tur, og gjøre klar til å kaste.

``` blocks
input.onButtonPressed(Button.AB, function(){})
```

## Steg 1
For å vise at det er din tur sender vi tallet ``2`` til den andre micro:biten. Vi setter også variabelen ``||variables:dinTur||`` til ``sann``, og viser en hake.

``` blocks
input.onButtonPressed(Button.AB, function(){
    radio.sendNumber(2)
    dinTur = true
    basic.showIcon(IconNames.Yes)
})
```

## Steg 2
Lag to variabler: ``||variables:kastNr||`` og ``||variables:antallKast||``. Sett dem til henholdsvis ``1`` og ``6``.

``` blocks
input.onButtonPressed(Button.AB, function(){
    radio.sendNumber(2)
    dinTur = true
    basic.showIcon(IconNames.Yes)
    kastNr = 1
    antallKast = 6
})
```

## Når ristes @showdialog
Når vi rister micro:biten kastes terningen.

``` blocks
input.onGesture(Gesture.Shake, function () {
	
})
```

## Steg 1
Først må vi sjekke om det er din tur, altså at ``||variables:dinTur||`` er ``sann``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
    
    }
})
```

## Steg 2
Vi setter inn ``||basic:tøm skjerm||`` og viser teksten ``Kast:``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
    }
})
```

## Steg 3a @showhint
Nå skal vi vise terningene vi kaster. Sett inn en ``||loops:gjenta for indeks fra 0 til 4||``. 

Siden vi skal telle antall terninger vi vil kaste så må bytte ut ``4`` med ``||variables:antallKast||`` ``- 1`` siden blokken teller fra null og ikke fra en.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= 4; indeks++) {}
    }
})
```

### Steg 3b
Gå til ``Matematikk``, finn ``||math:0 - 0||`` og sett inn den i stedet for ``4``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= 0 - 0; indeks++) {}
    }
})
```

### Steg 3c
Bytt ut første ``0`` med ``||variables:antallKast||``, og den siste ``0``-en med ``1``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= antallKast - 1; indeks++) {}
    }
})
```

## Steg 4a @showhint
Inne i ``gjenta``-blokken setter vi inn at vi skal vise tallet ``indeks + 1``, også en pause på et halvt sekund.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= antallKast - 1; indeks++) {
            basic.showNumber(0)
        }
    }
})
```

### Steg 4b
Bytt ut ``0`` med ``||math:0 + 0||`` fra ``matematikk``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= antallKast - 1; indeks++) {
            basic.showNumber(0 + 0)
        }
    }
})
```

### Steg 4c
Bytt ut første ``0`` med ``||variables:indeks||`` (dra den ned fra ``||loops:gjenta||``-blokken), og den andre med ``1``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= antallKast - 1; indeks++) {
            basic.showNumber(indeks + 1)
        }
    }
})
```

### Steg 4d
Sett til slutt inn pausen.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        basic.clearScreen()
        basic.showString("Kast:")
        for (let indeks = 0; indeks <= antallKast - 1; indeks++) {
            basic.showNumber(indeks + 1)
            basic.pause(500)
        }
    }
})
```

## Steg 5
På menyen ``Bilder`` finner du ``||images:show image myImage at offset 0||``. Sett den inn under ``||basic:pause (ms) 500||``.

![Show image](https://isimagan.github.io/yatzy/img/showImage1.png)

## Steg 6
``||variables:myImage||`` finnes ikke, så den må erstattes. Gå til ``Tabeller`` og finn blokken ``||tables:få en tilfeldig verdi fra list||``. Trykk på ``||variables:list||`` og bytt den med ``||variables:terning||``.

Fullfør med å sette inn en pause på 1 sekund.

![Show image](https://isimagan.github.io/yatzy/img/showImage2.png)

## Steg 7a @showhint
Under ``||loops:gjenta||``-blokken setter vi inn en ``||logic:hvis sann så||``-blokk.
Her skal vi sjekke om du enten har brukt opp alle kastene dine, eller om du har valgt å beholde alle terningene.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        if (true) {}
    }
})
```

### Steg 7b
Fra ``Logikk`` setter du inn ``||logic:eller||``. I begge de tomme feltene setter du inn ``||logic:0 = 0||``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        if (0 == 0 || 0 == 0) {}
    }
})
```

### Steg 7c
I den første ``||logic:0 = 0||``-blokken setter du inn ``||variables:antallKast||`` ``= 0``, og i den andre setter du inn ``||variables:kastNr||`` ``= 3``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        if (antallKast == 0 || kastNr == 0) {}
    }
})
```

## Steg 8
Hvis dette stemmer skal dette skje:
1. ``||variables:dinTur||`` skal være ``||logic:usann||``
2. Vi skal sende tallet 1
3. Vi skal vise et kryss.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        if (antallKast == 0 || kastNr == 0) {
            dinTur = false
            radio.sendNumber(1)
            basic.showIcon(IconNames.No)
        }
    }
})
```

## Steg 9
Trykk på ``+``-tegnet så du får opp ``ellers``. Inni her endrer vi ``||variables:kastNr||`` med ``1``.

``` blocks
input.onGesture(Gesture.Shake, function () {
    if (dinTur) {
        if (antallKast == 0 || kastNr == 0) {
            dinTur = false
            radio.sendNumber(1)
            basic.showIcon(IconNames.No)
        } else {
            kastNr += 1
        }
    }
})
```

## Avslutning når ristes @showdialog
Nå skal koden din se slik ut når micro:biten ristes.

![Når ristes](https://isimagan.github.io/yatzy/img/naarRistes.png)

## Når knapp B trykkes
Når ``||input:knapp B||`` trykkes skal vi endre hvor mange terninger du vil kaste.

``` blocks
input.onButtonPressed(Button.B, function(){})
```

## Steg 1
Antall terninger du vil kaste kan bare endres om det er din tur. Vi setter inn ``||logic:hvis||``-blokken igjen, og ser om det er din tur.

``` blocks
input.onButtonPressed(Button.B, function(){
    if (dinTur) {}
})
```

## Steg 2
Antall terninger du vil bruke vil være 6 hver gang det er din tur igjen. Hvis ``||variables:antallKast||`` er ``6`` så endres den til ``0``, hvis ikke økes den med ``1``.

``` blocks
input.onButtonPressed(Button.B, function(){
    if (dinTur) {
        if (antallKast == 6) {
            antallKast = 0
        } else {
            antallKast += 1
        }
    }
})
```

## Steg 3
Avslutt med å vise hvor mange terninger som er valgt.

``` blocks
input.onButtonPressed(Button.B, function(){
    if (dinTur) {
        if (antallKast == 6) {
            antallKast = 0
        } else {
            antallKast += 1
        }
        basic.showNumber(antallKast)
    }
})
```

## Når vi mottar et tall @showdialog
Siste vi skal programmere er når vi mottar et tall. Vi har programmert at dette skjer hvis vi mottar følgende tall:
- ``1``: Den andre spilleren har kastet, og det er din tur.
- ``2``: Den andre spilleren har startet spillet, men han/hun har ikke begynt å kaste terninger ennå.

``` blocks
radio.onReceivedNumber(function(receviedNumber){})
```

## Steg 1
Hvis ``||variables:receviedNumber||`` er ``1`` setter vi inn det samme som når vi starter spillet, bortsett fra at vi ikke sender noe nummer.
- ``||variables:dinTur||`` er ``||logic:sann||``
- Vi viser hake-ikonet
- ``||variables:kastNr||`` er 1
- ``||variables:antallKast||`` er 6

``` blocks
radio.onReceivedNumber(function(receviedNumber){
    if (receviedNumber == 1) {
        dinTur = true
        basic.showIcon(IconNames.Yes)
        kastNr = 1
        antallKast = 6
    }
})
```

## Steg 2
Hvis ``||variables:receviedNumber||`` ikke er ``1`` så må den være ``2``. Trykk på ``+``-knappen for å få opp ``ellers``, og vis kryss (som er vårt tegn på at det ikke er din tur)

``` blocks
radio.onReceivedNumber(function(receviedNumber){
    if (receviedNumber == 1) {
        dinTur = true
        basic.showIcon(IconNames.Yes)
        kastNr = 1
        antallKast = 6
    } else {
        basic.showIcon(IconNames.No)
    }
})
```

## Avslutning @showdialog
Dere er ferdig. Skal dere spille så husk å ha papir og blyant foran deg så du kan skrive ned kastene dine.
