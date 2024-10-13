### OpenwebRX  Installatie & Configuratie door ON3PDY. ###
---
## Benodigdheden ##
<img src="assets/images/rpi_board.jpg" width="300">      <img src="assets/images/pi5.png" width="300">

[**Raspberry Pi**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-5-4gb-11579?_gl=1*lkf79s*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Dit is een kleine singleboardcomputer met een ARM-processor.

Deze is in verkrijgbaar in verschillende versies.
Alle versies vanaf een V3 kunnen dienen voor dit project.

[**Behuizing & Koeling**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-behuizing-voor-pi-5-zwart-11584?_gl=1*1a7n6vn*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)

[**Voeding**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-27w-usb-c-power-supply-zwart-eu-11582?_gl=1*p4xdg9*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Voeding 5.1V - aansluiting en vermogen hangen af van de gebruikte Raspberry Pi versie.

[**SD kaart**](https://www.kiwi-electronics.com/nl/transcend-32gb-microsd-premium-class-10-uhs-i-plus-adapter-303?search=sd%20kaart)
MicroSD kaart minimaal 8Gb.

**S.D.R's**

SDR-dongles zijn oorspronkelijk ontworpen voor DVB-T HDTV-ontvangst, maar ze zijn prima bruikbaar als SDR.

[**RTL-SDR V3**](https://www.vandijkenelektronica.nl/product/rtl-sdr-v3-tcxo-dongle-500khz-1700mhz-sma-aansluiting/) (is wat ik in gebruik heb)

[**RTL-SDR V4**](https://www.vandijkenelektronica.nl/product/rtl-sdr-v4-tcxo-dongle-500khz-1700mhz-sma-aansluiting/) (geen ervaring mee!)

Persoonlijk heb ik deze modellen in mijn shack. 
- RTL-SDR
- SdrPlay

<img src="assets/images/rtl-sdr.jpg" width="150"><img src="assets/images/sdrplay.jpg" width="300">

**Programma's**
- [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- [Win32 Disk Imager](https://win32diskimager.org/)
- [balenaEtcher](https://balenaetcher.en.download.it/download)

---

## Installatie ##

Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/openwebrx/releases/)

Kies hier voor het zip bestand (voor V3 32bit voor V4 kan je ook de 64bit versie gebruiken) . **image_2024-08-26-OpenWebRX+-32bit-v1.2.67.zip**


Schrijf het bestand naar de **SD kaart** met behulp van het programma **Raspberry Pi Imager**

<img src="assets/images/rpi_im1.png" width="500">

## Instellen van systeem gebruiker & paswoord! ##

<img src="assets/images/settings_rpim.png" width="500">

Kies hier voor **AANPASSEN** om onderstaand dialoog te openen.

<img src="assets/images/rpi_im2.png" width="500">

- *Hostnaam* ==> vrije keuze voorbeeld: demoSDR
- *Gebruikersnaam* ==> vrije keuze voorbeeld: demoUSR
- *Wachtwoord* ==> vrije keuze demo (opgelet deze is alleen voor het OS)
- *Wiffi instellen* ==> kan je eventueel overslaan maar kan wel handig zijn om straks te configuren.
- Regio instellingen *Tijdzone:* **Europa/Brussels** en *Toetsenbord indeling:* **be**

Kies **Opslaan** om deze gegevens te bewaren en toe te passen.

<img src="assets/images/rpi_im3.png" width="500">

Klik op **ja** voor deze waarschuwing

mogelijk komt er een bestandsverkener scherm open (negeer waarschuwing en sluit dit)

<img src="assets/images/rpi_im4.png" width="500">
De image wordt nu op de SDkaart geinstalleerd.

<img src="assets/images/rpi_im5.png" width="500">
De installatie wordt geverifieerd

<img src="assets/images/rpi_im6.png" width="500">
Verwijder de SDkaart uit je PC en klik op VERDER GAAN

Om verbinding van op afstand te kunnen maken moet SSH nog worden geactiveerd.

Steek de SDkaart terug in je PC en maak een nieuw leeg tekstbestand aan in de root map met als naam **ssh** (zonder extentie!)

![image](assets/images/ssh.png)

**De eerste opstart van OpenWebRx**

- Steek de SD kaart in de Raspberry PI.
- Sluit de RPI aan in het netwerk.
- sluit de SDR dongle aan op 1 van de USB poorten.
- Sluit de voeding aan en wacht tot deze is opgestart.

Als alles goed is verlopen kan je nu de OpenWebRx openen in je netwerk. **http://demosdr.local:8073/**


## Inloggen op de Raspberry Pi vanop afstand ##
Via een computer in het zelfde netwerk als deze van de Raspeberry Pi kan je inloggen via **SSH** met het programma **PuTTY**.

Hiervoor heb je volgende gegevens voor nodig.
- IP adres van de Raspberry Pi of de hostname **(demosdr.local)**
- gebruikersnaam
- Wachtwoord

De gebruikersnaam en paswoord is wat je hebt opgegegeven in de 'Raspberry Pi Imager'

IP adres: hier moeten we eerst opzoek gaan naar wat er via DHCP is toegekend aan de Raspberry Pi.

Via de opdrachtpromt (CMD) kunnen we dit vinden: ping de hostname die je hebt opgegegeven in 'Raspberry Pi Imager'

`ping demoSDR`

![image](assets/images/ping.png)

<img src="assets/images/put_1.png" width="500">

De allereerste keer de PC een verbinding maakt krijg je dit scherm te zien. klik op JA om verder te gaan.

<img src="assets/images/put_2.png" width="500">

Eerst zorgen we dat het OS volledig up to date is. (de allereerste keer kan dit lang duren, geduld ...)

`sudo apt-get update`

`sudo apt-get upgrade -y`

`sudo reboot`

<img src="assets/images/ssh_1.png" width="500">

`sudo rpi-update` (**eenmalig** de firmware updaten als je werkt met een oudere V3 RPI)

Log opnieuw in op de RPI om een OpenWebRx admin web gebruiker en wachtwoord instellen.

`sudo openwebrx admin adduser XXXX` (XXXX vervangen door een gebruikersnaam en kies een paswoord)

<img src="assets/images/put_3.png" width="500">

Deze zijn ook interesante commando's betreft gebruiker administratie.

`sudo openwebrx admin adduser` [username]            Add a new user

`sudo openwebrx admin removeuser` [username]         Remove an existing user

`sudo openwebrx admin resetpassword` [username]      Reset a user's password

`sudo openwebrx admin disableuser` [username]        Disable a user

`sudo openwebrx admin enableuser` [username]         Enable a user

`sudo openwebrx admin listusers`                     List enabled users

`sudo openwebrx admin hasuser`                       Test if a user exists

### Installing digital modes ###

Nu we toch op het OS zijn ingelogd gaan we nog wat extra digitale decoders installeren. (niet verplicht)

`sudo install-softmbe.sh`

---

### Configureren van de WebSdr ###

**Settings ==> General Settings**

Receiver name = ON4TRV

Receiver location = Lubbeek, Belgium

Receiver elevation = 200

Receiver admin = info@trvrienden.be

Receiver band plan = ITU Region 1 (Africa, Europe, Middle East, North Asia)

Receiver coordinates 50,8821422       4,83844307581241

Photo title = Web SDR van de Toffe Radio Amateur Vrienden

Photo description = <IFRAME style=float:right marginWidth=0 marginHeight=0 src=https://www.dxfuncluster.com/widgets/cluster25.php frameBorder=1 scrolling=yes width=620 height=200></IFRAME>

Receiver Avatar + Receiver Panorama : upload bestanden

Allow users to change center frequency = aanvinken

Magic key = kies een wachtwoord indien je dit wenst. ==> http://localhost:8073/#freq=14000000,mod=usb,sql=-150 **,key=on4trv**

Waterfall color theme = Theme By Teejeez....

**Settings ==> SDR device settings**

<img src="assets/images/sdr_device_settings.png" width="800">
Schakel de Airspy HF+ en SDRPlay uit (tenzij je dergelijke SDR hebt)

**Settings ==> SDR device settings ==> RTL-SDR**

<img src="assets/images/RTL_sdr_settings.png" width="800">

Maak de verschillende frequentie banden aan die je wenst te gebruiken.

<img src="assets/images/PS_2m.png" width="800">
<img src="assets/images/PS_4m.png" width="800">
<img src="assets/images/PS_6m.png" width="800">
<img src="assets/images/PS_10m.png" width="800">
<img src="assets/images/PS_11m.png" width="800">
<img src="assets/images/PS_12m.png" width="800">
<img src="assets/images/PS_15m.png" width="800">
<img src="assets/images/PS_17m.png" width="800">
<img src="assets/images/PS_20m.png" width="800">
<img src="assets/images/PS_70cm_1.png" width="800">
<img src="assets/images/PS_70cm_2.png" width="800">
<img src="assets/images/PS_70cm_3.png" width="800">
<img src="assets/images/PS_70cm_4.png" width="800">
<img src="assets/images/PS_70cm_5.png" width="800">
<img src="assets/images/PS_adsb.png" width="800">
<img src="assets/images/PS_air.png" width="800">
<img src="assets/images/PS_ships.png" width="800">

---


### installing plugins ###
[openwebrxplus-plugins](https://github.com/0xAF/openwebrxplus-plugins)

Om een ​​plugin(s) te laden moet je een **init.js** bestand aanmaken in je openwebrx installatie.

Om de juiste map te vinden waar bestand moet staan, gebruik je volgend commando.  `sudo find / -name openwebrx.js`

`cd /usr/lib/python3/dist-packages/htdocs/plugins/receiver`    vervang **openwebrx.js** door **plugins/receiver**

Tip: wil je zien wat er in deze map staat gebruik **ls -a**

We kopieren het aanwezige voorbeeld naar een nieuw bestand met de juiste naam.  `sudo cp init.js.sample init.js`

Nu gaan we dit bestand editeren met het commando `sudo nano init.js`

Eerst maken we het bestand compleet leeg zet cursor bovenaan (CTRL+K)

schakel over naar RAW mode en kopier wat TUSSEN de 2 @ tekens staat in je klembord.

@

// Plugin initialization.
// First load the utils, needed for some plugins
Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/utils/utils.js').then(async function () {
  Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/utils/utils.js')
    .then(async function () {
    Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/frequency_far_jump/frequency_far_jump.js');
    await Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/notify/notify.js');
    Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/keyboard_shortcuts/keyboard_shortcuts.js');
    Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/map/layer_qth_maidenhead/layer_qth_maidenhead.js');
    Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/sort_profiles/sort_profiles.js');
    Plugins.load('https://0xaf.github.io/openwebrxplus-plugins/receiver/tune_checkbox/tune_checkbox.js');
  });
});

@

CTRL+X ==> save modified buffer Yes

sudo systemctl restart varnish nginx

---

Aanbevolen is de RPI een vast IP adres geven. (niet verplicht)

Hiervoor doen we eerst wat opzoeken betrefende het netwerk waarmee we verbonden zijn.

Opniew gebruiken we hiervoor de opdrachtprompt (CMD)  

`ipconfig`

Scrol tot je de gegevens van de *Ethernet adapter* ziet. Noteer hier de **Default Gateway**
![image](assets/images/cmd_2.png)

nu zijn we klaar om via **PuTTY** de instelling van de RPI aan te passen. Hiervoor heeft de RPI een ingebouwde editor. **NANO**

`sudo nano /etc/dhcpcd.conf`

zoek naar **Example static IP configuration van interface eth0** verwijder de # vooraan en pas het voorbeeld aan.

![image](assets/images/ip_2.png)

TIP: gebruik als static ip_address dat wat via DHCP is toegekend aan de Raspberry Pi. (zo ben je zeker van geen conflicten!).

static routers en static domain_name_servers daar gebruik je de **Default Gateway** die je hebt verkregen via **ipconfig**

- static ip_address=192.168.1.47/24 (opgelet /24 moet achteraan het gewenste IP adres staan!)
- static routers=192.168.1.1
- static domain_name_servers=192.168.1.1

Sluit af met de toetsencombinatie **CTRL+X** en bevestig met **Y**

---
**SDR op het internet**

Maak een gratis account aan op [ClouDNS](https://www.cloudns.net) tenzij je een domeinnaam bezit dan kan je deze gebruiken.

Maak een gratis account aan op [Cloudflare](https://dash.cloudflare.com)

In Cloudflare krijg je na het toevoegen van je domain (aangemaakt in ClouDNS) 2 naamservers.

Deze moeten we nu registreren in ClouDNS toevoegen als NS voor elke naam die je wenst te gebruiken.

Als alles goed is (kan enige tijd duren!) staat er bovenaan bij Cloudflare onder websites bovenaan in het groen Active.

Terug naar de Raspberry Pi.

`sudo apt install curl lsb-release`

`curl -L https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-archive-keyring.gpg >/dev/null`

`echo "deb [signed-by=/usr/share/keyrings/cloudflare-archive-keyring.gpg] https://pkg.cloudflare.com/cloudflared $(lsb_release -cs) main" | sudo tee  /etc/apt/sources.list.d/cloudflared.list`

`sudo apt update`

`sudo apt install cloudflared`

--- NOT ON SD ---

Log in op je Cloudflare account en hou deze op de achtergrond open!.

`sudo cloudflared tunnel login`

Na het inbrengen van het bovenstaande commando krijg je een URL knip en plak deze in een nieuw tabblad in je browser.

https://dash.cloudflare.com/argotunnel?aud=&callback=https%3A%2F%2Flogin.cloudflareaccess.org%2FC7_Sna9w_6j4N3RY3DIpas4q_QU4jbKlGZL13urHHlU%3D

volg de stappen, sluit de pagina en wacht tot het cert is geinstalleerd.

`sudo cloudflared tunnel create SDR_1`

je krijgt nu de melding  **Created tunnel SDR with id PP9061c4ac-903c-4fb5-ae05-MM** (bewaar deze id!)  

`sudo cloudflared tunnel route dns SDR_1 sdr.pats.dns-cloud.net`


Routing the Tunnel to a Domain Name   (http://192.168.1.37:8073) cloudflared tunnel run --url localhost:PORT TUNNELNAME
`sudo cloudflared tunnel run --url http://localhost:8073 SDR_1`


**Connecting to your Cloudflare Tunnel on Boot**

sudo mkdir /home/demoUSR/.cloudflared
	
sudo nano /home/demoUSR/.cloudflared/config.yml

pas onderstaande aan naar je eigen situatie. (in kladblok voorbereiden)

tunnel: [TUNNELNAME]
credentials-file: /root/.cloudflared/[UUID].json

ingress:
    - hostname: [HOSTNAME]
      service: [PROTOCOL]://localhost:[PORT]
    - service: http_status:404

==> aangepaste versie tussen de 2 @

@
tunnel: SDR_1
credentials-file:  /root/.cloudflared/[UUID].json

ingress:
    - hostname: sdr.pats.dns-cloud.net
      service: http://localhost:8073
    - service: http_status:404
@

`sudo nano ~/.cloudflared/config.yml`

Plak in het geopende bestand de voorbereide informatie en sluit met CTRL+X bevestig met Y en enter.

`sudo cloudflared --config ~/.cloudflared/config.yml service install`

`sudo systemctl enable cloudflared`

`sudo systemctl start cloudflared`

---

**BACKUP maken !!!**

hiervoor gebruik ik Win32 Disk Imager. 

Navigeer naar een folder en geef een zinvolle bestandsnaam op gevolgd door **.img**

Selecteer het juiste doelapparaat. Klik op Lezen en wacht tot het inlezen voltooid is.

<img src="assets/images/winD32.png" width="500">

Bewaar dit op een veilige plaats Tip: bewaar ook de login gegevens op die plaats in een tekstbestand.


---


**VIA reeds opgeslagen backup**

Hiervoor gebruik ik balenaEtcher (niet nodig om een zip of rar bestand uit te pakken)
<img src="assets/images/etcher.png" width="700">

Na het schrijven de SDkaart terug in de RPI plaatsen en opstarten.

Krijg je onderstaande klik op annuleren en sluit het scherm.

<img src="assets/images/error.png" width="300">


**Interesante links**
[Cheatsheets/Learn Raspberry Pi](https://www.codecademy.com/learn/learn-raspberry-pi/modules/raspberry-pi-command-line-module/cheatsheet)















