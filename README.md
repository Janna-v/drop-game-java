# Drop Game

Piccola demo desktop in Java e libGDX: il giocatore sposta un contenitore per raccogliere le gocce che cadono dall'alto.**Demo individuale di apprendimento, realizzata seguendo un tutorial.** L’obiettivo è esercitarmi con Java e libGDX attraverso input, animazione, collisioni e audio. Il progetto mantiene l’ambito di una piccola demo guidata: non è pensato come videogioco completo con livelli, progressione e tutte le funzionalità di un prodotto finito. Le funzionalità presenti e le osservazioni tecniche riportate di seguito descrivono lo stato effettivo del codice.

## Funzionalità implementate

- Creazione periodica delle gocce in posizioni orizzontali casuali.
- Movimento del contenitore tramite tastiera e puntatore premuto.
- Limiti orizzontali al movimento.
- Rilevamento delle collisioni tramite rettangoli.
- Rimozione delle gocce raccolte o uscite dallo schermo.
- Sprite, immagine di sfondo, musica in ripetizione ed effetto sonoro alla raccolta.
- Adattamento della vista tramite `FitViewport`.

## Comandi

- **Freccia sinistra:** movimento mentre il tasto è premuto.
- **Freccia destra:** piccolo spostamento a ogni nuova pressione, secondo l'implementazione attuale.
- **Puntatore premuto:** il contenitore segue la coordinata orizzontale del puntatore.

## Tecnologie e struttura

Java, libGDX 1.14.0, Gradle e LWJGL3.

- `core/src/main/java/it/giovanna/drop/Main.java`: logica, input e disegno.
- `lwjgl3/`: avvio desktop e configurazione della distribuzione.
- `assets/`: immagini e audio.
- `gradle/` e `gradlew.bat`: configurazione e wrapper Gradle.

## Avvio desktop

La configurazione del daemon Gradle indica una toolchain Java 17. Predisporre un JDK 17 e una connessione per scaricare le dipendenze.

In PowerShell, dalla radice del repository:

```powershell
.\gradlew.bat lwjgl3:run
```

Per generare il JAR desktop:

```powershell
.\gradlew.bat lwjgl3:jar
```

L'output viene prodotto in `lwjgl3/build/libs`. Su macOS/Linux si usa `./gradlew` al posto di `.\gradlew.bat`.

## Limiti della demo

Non sono implementati punteggio, livelli o una schermata di fine partita nella classe principale analizzata. `pause()` e `resume()` lanciano `UnsupportedOperationException`; `dispose()` non libera ancora le risorse. La gestione del ciclo di vita è quindi da completare.

Le istruzioni derivano dal codice e dai task Gradle; avvio e build non sono stati eseguiti durante questa revisione.
