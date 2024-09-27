# OpenwebRX
### Installatie & Configuratie OpenwebRx door ON3PDY.
---
## Benodigdheden
<img src="assets/images/rpi_board.jpg" width="300">      <img src="assets/images/pi5.png" width="300">

[**Raspberry Pi**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-5-4gb-11579?_gl=1*lkf79s*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Dit is een kleine singleboardcomputer met een ARM-processor. (afbeelding hier boven)
Deze zijn verkrijgbaar in verschillende versies.

Alle versies hoger dan een V3 kunnen dienen voor dit project.

[**Behuizing**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-behuizing-voor-pi-5-zwart-11584?_gl=1*1a7n6vn*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
behuizing voor de Raspberry Pi 5 met ventilator, wordt gevoed en bediend via de speciale connector op de Raspberry Pi 5. +-10,95€

[**Voeding**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-27w-usb-c-power-supply-zwart-eu-11582?_gl=1*p4xdg9*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
27 Watt USB-C voeding 5.1V - 5A. +- 12,95€

[**SD kaart**](https://www.kiwi-electronics.com/nl/transcend-32gb-microsd-premium-class-10-uhs-i-plus-adapter-303?search=sd%20kaart)
MicroSD kaart 32Gb (minimaal 8Gb is voldoende +- 11,25€)

**S.D.R's**

[RTL-SDR V3](https://www.vandijkenelektronica.nl/product/rtl-sdr-v3-tcxo-dongle-500khz-1700mhz-sma-aansluiting/)
RTL-SDR-dongles zijn oorspronkelijk ontworpen voor DVB-T HDTV-ontvangst, maar ze zijn ook bruikbaar als SDR. +- 40€

[RTL-SDR V4](https://www.vandijkenelektronica.nl/product/rtl-sdr-v4-tcxo-dongle-500khz-1700mhz-sma-aansluiting/) +- 47.50€ (geen ervaring mee!)

Persoonlijk heb ik deze 3 modellen in mijn shack. 
- RTL-SDR
- NooElec
- SdrPlay

<img src="assets/images/RTL-SDR_.jpg" width="150"><img src="assets/images/sdrplay.jpg" width="300"><img src="assets/images/nooelec.png" width="300">

*kosten van het hele project ligt +- rond de 150€ afhankelijk van de gemaakte keuze's*

**Programma's**
- [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

### Installatie ###

Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/ppa)

Schrijf het bestand naar de **SD kaart** of **USB stick** met behulp van **Raspberry Pi Imager**

<img src="assets/images/rpim.png" width="500">

## Instellen van systeem gebruiker & paswoord! ##

<img src="assets/images/settings_rpim.png" width="500">

Kies hier voor **AANPASSEN** om onderstaand dialoog te openen.

<img src="assets/images/rpim_settings.png" width="500">

- *Hostnaam* ==> vrije keuze voorbeeld: OpenwebRX
- *Gebruikersnaam* ==> vrije keuze voorbeeld: sdr
- *Wachtwoord* ==> vrije keuze (opgelet deze is alleen voor het OS)
- *Wiffi instellen* ==> kan je eventueel overslaan maar kan wel handig zijn om straks te configuren.
- Regio instellingen *Tijdzone:* Europa/Brussels en *Toetsenbord indeling:* be

kies **Opslaan** om deze gegevens te bewaren en toe te passen.

Om verbinding van op afstand te kunnen maken moet SSH worden geactiveerd.

Maak een nieuw leeg tekstbestand aan in de root map en deze te hernoemen naar ssh (zonder extentie!)

![image](assets/images/ssh.png)

Steek de SD kaart in de Raspberry PI en wacht tot deze is opgestart.

## Inloggen op de Raspberry Pi vanop afstand ##
Via een computer in het zelfde netwerk als de Raspeberry Pi kan je inloggen via het programma **PuTTY**.

hiervoor heb je volgende gegevens voor nodig.
- IP adres van de Raspberry Pi
- gebruikersnaam
- Wachtwoord

De gebruikersnaam en paswoord is wat je hebt opgegegeven in de 'Raspberry Pi Imager'

IP adres: hier moeten we eerst opzoek gaan naar wat er via DHCP is toegekend aan de Raspberry Pi.

Via de opdrachtpromt kunnen we dit vinden: ping de hostname die je hebt opgegegeven in 'Raspberry Pi Imager'
![image](assets/images/cmd.png)

Aanbevolen is de RPI een vast IP adres geven zodat je niet steeds deze moet gaan zoeken.

`sudo nano /etc/dhcpcd.conf`

zoek naar onderstaande verwijder # en pas het voorbeeld aan

interface eth0
static ip_address=192.168.1.47/24 (maak hier een unieke keuze in je netwerk voor de laatste cijfers voor /24)
static routers=192.168.1.1
static domain_name_servers=192.168.1.1

Eerst zorgen we dat het OS volledig up to date is.
`sudo apt-get update`

`sudo apt-get upgrade -y`

nu gaan we herstarten om dit alles te activeren.

`sudo reboot`

`sudo rpi-update` (eenmalig de firmware updaten als je werkt met een oudere RPI)

OpenWebRx web gebruiker en wachtwoord instellen (web interface)

`sudo openwebrx admin adduser XXXX` (XXXX vervangen door een gebruikersnaam en kies een paswoord)

`sudo openwebrx admin adduser` [username]            Add a new user

`sudo openwebrx admin removeuser` [username]         Remove an existing user

`sudo openwebrx admin resetpassword` [username]      Reset a user's password

`sudo openwebrx admin disableuser` [username]        Disable a user

`sudo openwebrx admin enableuser` [username]         Enable a user

`sudo openwebrx admin listusers`                     List enabled users

`sudo openwebrx admin hasuser`                       Test if a user exists


#installing digital modes

sudo install-softmbe.sh



**installing plugins**
https://github.com/0xAF/openwebrxplus-plugins
To load a plugin you need to create init.js file inside your openwebrx installation under htdocs/plugins/{type} folder. 
You can find the folder with this command:
`find / -name openwebrx.js`

You need to create/edit the init.js.
In the next example we will load receiver plugins.
First we need to create the init.js file:

OWRX_FOLDER=$(dirname `find / -name openwebrx.js`)
cd "$OWRX_FOLDER/plugins/receiver"
cp init.js.sample init.js
$EDITOR init.js


http://localhost:8073/



