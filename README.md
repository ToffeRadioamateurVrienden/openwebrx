# OpenwebRX
### Installatie & Configuratie OpenwebRx door ON3PDY.
---
## Benodigheden
<img src="assets/images/rpi_board.jpg" width="300">   <img src="assets/images/pi5.jpg" width="300">

[**Raspberry Pi**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-5-4gb-11579?_gl=1*lkf79s*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Dit is een kleine singleboardcomputer met een ARM-processor.
Deze zijn verkrijgbaar in verschillende versies aanbevolen is een **Raspberry Pi 5 - 4GB**. +- 66,95€ **8Gb** kan ook maar deze is +-20€ duurder.

[**Behuizing**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-behuizing-voor-pi-5-zwart-11584?_gl=1*1a7n6vn*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
behuizing voor de Raspberry Pi 5 met ventilator, wordt gevoed en bediend via de speciale connector op de Raspberry Pi 5. +-10,95€

[**Voeding**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-27w-usb-c-power-supply-zwart-eu-11582?_gl=1*p4xdg9*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
27 Watt USB-C voeding 5.1V - 5A. +- 12,95€

[**SD kaart**](https://www.kiwi-electronics.com/nl/transcend-32gb-microsd-premium-class-10-uhs-i-plus-adapter-303?search=sd%20kaart)
MicroSD kaart 32Gb (minimaal 8Gb is voldoende +- 11,25€

**S.D.R's**
[RTL-SDR V3](https://www.vandijkenelektronica.nl/product/rtl-sdr-v3-tcxo-dongle-500khz-1700mhz-sma-aansluiting/)
RTL-SDR-dongles zijn oorspronkelijk ontworpen voor DVB-T HDTV-ontvangst, maar ze zijn ook bruikbaar waren als SDR. +- 40€

Hier zijn verschillende keuze's mogelijk, zo heeft elke sdr voordelen of nadelen. (prijs, bereik, enz.)

Persoonlijk heb ik deze 3 modellen in mijn shack. 
- RTL-SDR
- NooElec
- SdrPlay

<img src="assets/images/RTL-SDR_.jpg" width="150"><img src="assets/images/sdrplay.jpg" width="300"><img src="assets/images/nooelec.png" width="300">

**Programma's**
- [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
- [Angry IP Scanner](https://github.com/angryip/ipscan/releases/download/3.9.1/ipscan-3.9.1-setup.exe)



### Installatie ###

Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/ppa)

Schrijf het bestand naar de **SD kaart** of **USB stick** met behulp van **Raspberry Pi Imager**

<img src="assets/images/rpim.png" width="500">

## Instellen van systeem gebruiker & paswoord!

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

## Hoe benaderen en inloggen op de Raspberry Pi? ##
Via een computer in het zelfde netwerk als de Raspeberry Pi kan je inloggen via het programma **PuTTY**.

hier heb je volgende gegevens voor nodig.
- IP adres van de Raspberry Pi
- gebruikersnaam
- Wachtwoord

De gebruikersnaam en paswoord zijn wat je hebt opgegegeven in de 'Raspberry Pi Imager'

IP adres: hier moeten we eerst opzoek gaan naar wat er via DHCP is toegekend aan de Raspberry Pi.

Via de opdrachtpromt kunnen we dit vinden: ping de hostname dit heb je ook opgegegeven in de 'Raspberry Pi Imager'
![image](assets/images/cmd.png)


`sudo nano /etc/dhcpcd.conf`
zoek naar en pas het voorbeeld aan

interface eth0
static ip_address=192.168.1.47/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1


eerst zorgen we dat het OS volledig up to date is.
sudo apt-get update
sudo apt-get upgrade
sudo rpi-update (eenmalig de firmware updaten)
sudo openwebrx admin adduser SDR (kies een paswoord)
sudo reboot
#installing digital modes
sudo install-softmbe.sh
#installing plugins
https://github.com/0xAF/openwebrxplus-plugins

ifconfig
http://localhost:8073/



---
# Markdown Cheat Sheet

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax/) and [extended syntax](https://www.markdownguide.org/extended-syntax/).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

# H1
## H2
### H3

### Bold

**bold text**

### Italic

*italicized text*

### Blockquote

> blockquote

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- First item
- Second item
- Third item

### Code

`code`

### Horizontal Rule

---

### Link

[Markdown Guide](https://www.markdownguide.org)

### Image

![alt text](https://www.markdownguide.org/assets/images/tux.png)

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

### Fenced Code Block

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Footnote

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

### Heading ID

### My Great Heading {#custom-id}

### Definition List

term
: definition

### Strikethrough

~~The world is flat.~~

### Task List

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

### Emoji

That is so funny! :joy:

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight

I need to highlight these ==very important words==.

### Subscript

H~2~O

### Superscript

X^2^
