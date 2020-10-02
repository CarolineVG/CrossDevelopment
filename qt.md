# Cross Development - QT
## Intro
blablabla
## Gevolgde stappen
### 1. - Virtual Machine Linux aanmaken

Maak een nieuwe VM aan, met 6144MB memory kom je normaal toe.

### 2. - MXE requirements en Download
Volg de stappen van deze tutorial (https://mxe.cc/#tutorial ) om MXE correct te installeren op de VM.

#### 2.1 Requirements
De virtual machine moet voldoen aan alle MXE's requirements, anders gaat het programma niet werken. We moeten verschillende zaken nog installeren, naargelang wat er reeds op u systeem staat. Geef volgende code in om de requirements te installeren.

> apt-get install \
    autoconf \
    automake \
    autopoint \
    bash \
    bison \
    bzip2 \
    flex \
    g++ \
    g++-multilib \
    gettext \
    git \
    gperf \
    intltool \
    libc6-dev-i386 \
    libgdk-pixbuf2.0-dev \
    libltdl-dev \
    libssl-dev \
    libtool-bin \
    libxml-parser-perl \
    lzip \
    make \
    openssl \
    p7zip-full \
    patch \
    perl \
    python \
    ruby \
    sed \
    unzip \
    wget \
    xz-utilscode

    Error: unable to acquire the dpkg frontend lock...
    Betekenis: het update programma van ubuntu is nog aan het updaten.
    Oplossing: wacht tot alle updates klaar zijn, en voer het commando opnieuw uit.

#### 2.1 Download
Download de huidige versie van MXE via github.
>git clone https://github.com/mxe/mxe.git

De stap 'System Wide Installation' van de tutorial slaan we over, aangezien we MXE in onze home directory willen installeren.

### 3. Build MXE
Nu we MXE gedownload hebben, gaan we deze builden. Geef volgend commando in. Het uitvoeren van dit commando kan een tijdje duren, bij mij heeft het een 40tal minutjes geduurd.
> make cc

    Error: No rule to make target 'cc'
    Betekenis: We zitten niet in de juiste map (mxe)
    Oplossing: Ga in de map mxe, en voer het commando opnieuw uit.

    Error: 
    Betekenis:
    Oplossing: 

Daarna voer je het volgende commando uit, ook dit commando nam een kwartiertje in beslag.
> make qtbase


### 4. Environment Variable aanpassen
Verander de PATH variabele zodat Linux weet waar MXE geïnstalleerd is.
> export PATH=/home/caroline/mxe/usr/bin:$PATH


### 5. Cross Compileren (QT)
In deze stap van de tutorial gaan we de compilatie uitvoeren. Zorg ervoor dat bij je VM settings 'shared clipboard' en 'drag n drop' op bidirectional staan, zodat je makkelijk bestanden vanuit je Windows PC naar je Linux machine kan kopiëren. 

![settings](/img/settings.png)

Kopieer eerst je testcase die je wil cross-compileren naar je Linux machine. 

    Probleem: De map van de testcase is gekopieerd, maar de inhoud van de map niet. 
    Oplossing: Selecteer de inhoud en sleep deze naar Linux.
    
Ga naar de map waar je testcase instaat, en voer het make commando uit
> /home/caroline/mxe/usr/i686-w64-mingw32.static/qt5/bin/qmake
    
    Error: img 'clock' is not found in /res...
    Probleem: Bij het kopieren van de testcase is de inhoud van de /res folder niet mee gekopieerd. 
    Oplossing: Selecteer de inhoud en sleep deze naar Linux.

De compilatie is nu voltooid!


### 6. Shared folder aanmaken
We maken nu een gedeelde map aan, zodat we vanuit onze Windows PC onze applicatie kunnen raadplegen.

Pas eerst je settings van je VM aan. Klik bovenaan op Devices -> Insert Guest Additions CD Image -> Run.

Daarna gaan we onze shared folder settings aanpassen. Klik op Devices -> Shared Folders -> Shared Folders Settings.
Maak aan nieuwe folder aan. Vul volgende zaken in:
* Folder path: path op Windows
* Folder name: naam 'app' op Windows
* Auto mount aanvinken
* OK

![addsharedfolder](/img/add_new_shared_folder.png)

Open nu de terminal in Linux, en maak een nieuwe map aan in Linux
>mkdir app-windows

Link de map met de map die je hebt gemaakt op Windows.
>sudo mount -t vboxsf app app-windows

* app: map op Windows
* app-windows: map op Linux

De shared folder is nu aangemaakt, dit kan je ook zien bij de instellingen van je VM. 

![sharedfolder](/img/shared_folders.png)




### 7. Run je programma op Windows
Ga op je Windows PC naar de locatie waar je de gedeelde map hebt aangemaakt. Nu zie je dat de inhoud van de map overeenkomt met de inhoud van de Linux map. Klik op 
* app (naam van de map)
* QtTimeTimer (naam van de applicatie)
* Release
* TestCase.exe (executable)

![result](/img/program_windows.png)

Je programma runt nu op je Windows PC, het cross compileren is geslaagd!


## Eventuele aanpassingen aan het concept


## Link met theorieles


## Screenshots eindresultaat


## Extra's 
### Gebruikte sites:
* https://mxe.cc/#tutorial
* https://mxe.cc/#requirements
* https://itsfoss.com/could-not-get-lock-error/
* https://github.com/google/or-tools/issues/380

