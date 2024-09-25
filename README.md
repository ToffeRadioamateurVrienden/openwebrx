# OpenwebRX
### Installatie & Configuratie OpenwebRx door ON3PDY.
---
## Benodigheden
[**Raspberry Pi**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-5-4gb-11579?_gl=1*lkf79s*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
Als platform gebruiken we een Raspberry Pi, dit is een kleine singleboardcomputer met een ARM-processor.
Deze is verkrijgbaar in verschillende versies aanbevolen is een **Raspberry Pi 5 - 4GB**. +- 66,95€

[**Behuizing**](https://www.kiwi-electronics.com/nl/raspberry-pi-boards-behuizingen-uitbreidingen-en-accessoires-59/raspberry-pi-behuizing-voor-pi-5-zwart-11584?_gl=1*1a7n6vn*_up*MQ..&gclid=CjwKCAjw6c63BhAiEiwAF0EH1Hk4vvkVqG9C-TbIWwtMIr4HgenyoZ5aiTEVGVtE6QI5oQILqpdzXhoClmwQAvD_BwE)
zwarte behuizing voor de Raspberry Pi 5 Hij bevat een ventilator met variabele snelheid, die wordt gevoed en bediend via de speciale connector op de Raspberry Pi 5

**SD kaart**

<img src="assets/images/rpi_board.jpg" width="300">

**S.D.R's**

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



## Installatie 

Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/ppa)

Schrijf het bestand naar een **SD kaart** of **USB stick** met behulp van **Raspberry Pi Imager**

<img src="assets/images/rpim.png" width="500">

## Instellen van systeem gebruiker & paswoord !

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
Tip: als de hostnaam niet zichtbaar is. verwijder de raspberry Pi uit het netwerk scan, breng terug in netwerk en scan opnieuw.

Via het programma **Angry IP Scanner** kunnen we dit vinden via de hostname ook dit opgegegeven in de 'Raspberry Pi Imager'

`sudo raspi-config` om de hostnaam eventueel te wijzigen

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
