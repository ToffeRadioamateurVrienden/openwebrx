# OpenwebRX
###Configuratie voor openwebRX door ON3PDY.
---
Download de laatste versie via volgende link: [OpenwebRx luarvique](https://github.com/luarvique/ppa)

Schrijf het bestand naar een SD kaart met behulp van [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

<img src="assets/images/rpim.png" width="500">

Om verbinding van op afstand te kunnen maken moet SSH worden geactiveerd.
dit doe je door na het schrijven van de SD kaart een nieuw leeg tekstbestand te maken en te hernoemen naar ssh (zonder extentie!)
![image](https://github.com/user-attachments/assets/9b5cc6b1-54db-4382-b13e-c151c4910631)
steek de SD kaart in de Raspberry PI en wacht tot de tekst op het scherm gestopt is
log in met de gebruikersnaam en paswoord dat is opgegegeven in 'Raspberry Pi Imager'
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
