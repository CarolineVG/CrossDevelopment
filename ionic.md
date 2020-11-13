# Cross Development - Ionic
## Intro
Als we Ionic gebruiken om te cross-compileren, moeten we eerst de testcase omzetten naar een webtaal. Aangezien ik voor QT de testapplicatie van de docent mocht gebruiken, herschrijf ik nu deze applicatie in Angular. 

## Gevolgde stappen
### 1. - dlqsf

We maken gebruik van Capacitor, dit is .......
Nu gaan we over de stappen die nodig zijn om de Ionic App te testen in een Android Emulator.
Zorg ervoor dat Android Studio geïnstalleerd is op je computer. Zo hebben we toegang tot het build systeem Gradle, de juiste SDK en een geschikt Android Virtual Device.


Eventuele plugins toevoegen
Capacitor maakt gebruik van plugins zodat de applicatie toegang heeft tot de native API. Zo kunnen we toegang krijgen tot het systeem, de camera, storage,...
Voor de Timer Applicatie maak ik gebruik van de plugin Modals, om een alert te sturen wanneer de timer is afgelopen. 

plugin testen in emulator (live reload)

installeer eerst de dependancy
npm install -g @ionic/cli native-run cordova-res

kijk na of je een @capacitor map hebt in node_modules
indien niet: voeg toe via volgend commando: ionic integrations enable capacitor

doe een build
ionic build

start de live reload sessie op
ionic cap run android -l --external

Android wordt opgestart
AndroidManifest aanpassen: de development server gebruikt geen https maar http. Android heeft hier problemen mee vanaf API level 28 of hoger. In de manifest laten we http toe via volgende code
<application
  android:usesCleartextTraffic="true"
>



## Eventuele aanpassingen aan het concept


## Link met theorieles


## Screenshots eindresultaat


## Extra's 
### Gebruikte sites:
