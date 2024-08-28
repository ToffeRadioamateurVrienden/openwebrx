# openwebRX
Configuratie voor openwebRX
Download the latest version https://github.com/luarvique/ppa
Schrijf het gedownloade document naar de SD kaart met behulp van 'Raspberry Pi Imager'
![image](https://github.com/user-attachments/assets/a2cbbe6c-5f7d-4a47-960b-625cb9bce29c)


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

