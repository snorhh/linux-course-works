# Virtual Boxin ja Linuxin asennus



Klo 13:50 
Latasin Debian Iso imagen, tiedosto debian-live-12.6.0-amd64-xfce.iso 
sivulta https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/ (n. 3GB)

Sen jälkeen latasin Virtual Boxin sivulta https://www.virtualbox.org/wiki/Downloads
kohdasta VirtualBox 7.0.20 platform packages-Windows hosts (n. 100 MB)

Suoritin ladatun .exe.tiedoston
click next, seuraavassa click next
Warning: Network interfaces, click Yes
duckduckasin Python core package win32.api virtual box
sivu https://www.sysnettechsolutions.com/en/fix-python-win32api-virtualbox/
Sivun ohjeiden perusteella latasin sivulta https://www.python.org/downloads/ 
tiedoston python-3.12.5-amd64.exe ja ajoin admin.oikeuksilla
ja klikkasin boksit "use admin privileges when installing py.exe" sekä "add python to Path"
(kuva 2)
klo 14:16
sivun ohjeen mukaan avasin powershellin admin-oikeuksilla 
Tässä vaiheessa kysyin ChatGPT:ltä, että mitä komento "Now, open PowerShell/CMD as admin, and type “py -m pip install pywin32” to install pywin32." tekee. ChatGPT ei ainakaan sanonut sen olevan mitenkään haitallinen, joten suoritin sen PowerShellissa. 
(En nähnyt pip-päivitystä, joten en tehnyt kohtaa 4)

14:22- uusi VirtualBox-asennusyritys, eli suoritan virtualbox.exen admin-oikeuksilla
Taas klikkasin kaksi kertaa next, varoituksesta next, Custom Setup-kohdast jätin kaikki valituiksi (Create start menu entries etc). Sen Jälkeen "Click installation". Tämän jälkeen klikkasin Finish.TAUKO
Tauko alkaa 14:27-15:30
15:30 jatkuu
Avasin Virtual Boxin
Machine...new, Create virtual Machine
, expert mode
Laitoin Name: Linux2024, hain ISO-imagen kansiosta,
Type Linux, version Debian (64 bit), klikkasin boksin
Skip unattended installation
HUOM, jos tässä kohtaa ei laittanut ISO-imagea, niin kohta "Skip unattended Installation" on harmaan.a
Kohdasta hardware: laitoin 2048MB
en klikannut "Enable EFI (special OSes only)
Hard disk -kohta: Create a Virtual Hard Disk Now
Hard Disk Size 60,00 GB
Hard Disk Type and Variant (default eli VDI (Virtual Box Image)
Toisin kuin ohjeessa, kohdassa ei ollut valintaa "Dynamically allocated" vaan "Pre-allocate Full Size", jota en valinnut.
Tämän jälkeen klikkasin Finish.
Klo 15:55
Ohjeissa tämän jälkeen tulisi lisätä ISO Virtual Boxin
kohdassa Settings, Storage ja Controller:IDe-alle, mutta se siis on jo siellä.
klo 15:59
Tuplaklikkasin Linux2024-kuvaketta Virtual Boxissa.
Ilmestyi ikkuna Debian 12, josta valitsin ensimmäisen eli Live
Ruutu meni hetkeksi mustaksi ja sitten Desktop tuli näkyviin.
Pari huomautusruutua tuli, en ehtinyt niihin reagoida.
klo 16:03 Ylävasemmalta "Applications"-kohdasta avasin Web Browsering, ja kokeilin että netti toimii.
Suljin selaimen.
16:07:
Klikkasin ikonia Install Debian.
Tuli varoitus, klikkasin "Run anyway"
Welcome-sivun language jätin default, American English ja klikkasin Next
Aikavyöhyke-kartasta valitsin Europe/Helsinki ja Next
Keyboard Model otin defaultin eli Generic 105-key PC, joka oli vähän erilainen kuin ohje, joissa oli lisäksi (intl.)
Vasemmalta valikosta otin Finnish ja oikeaan valikkoon jätin Default.
Tässä kohtaa Core Temp 1.18.1. valitti, että yksi tai kaksi prosessoria ylittivät itseni laittamat maksimilämpötilat, joten irrotin virtapiuhan koneesta.

16:15: Seuraava kohta, Erase disk ja jätin Boot loader location defaultiin eli Master Boot record of VBOX Harddisk
Next
Laitoin oman nimeni, login-nimeksi sanna, koneen nimeksi
forte16 ja salasanan. Log in without password...no.
Next
16:23 INSTALL
16:34 All done. Restart now? valittuna ja Done.
Aluksi tuli hämäävästi Debian-desktop, mutta jonkin ajan päästä näkyy login-ikkuna
16:39
ilmoitus:
Ibus Notification
Keymap changes do not work in Plasma Wayland at present. Please use systemsettings5 instead.
Googlasin ja löysin keskustelun, jonka perusteella päätin jättää välittämättä siitä. 
https://lists.debian.org/debian-input-method/2024/02/msg00040.html
16:45 avasin nettiselaimen ja tarkistin että netti toimii
tsekkasin paljonko on muistia
Avasin Terminal Emulatorin
kirjoitin "sudo apt-get update" sen jälkeen laitoin salasanan. Se lataili kaikenlaista.
16:48: kirjoitin "sudo apt-get -y dist-upgrade", ei kysynyt salasanaa ja lataili vielä enemmän tavaraa. 
16:54 kysyi salasanaa, jonka laitoin, sen jälkeen tekee jotain setuppeja ehkä noin minuutin
16:56 asensin palomuurin "sudo apt-get -y install uf"'ja "sudo ufw enable" minkä jälkeen näkyi teksti "Firewall is active and enabled on system startup"
17:00 Appplications, logout, restart (poistin ruksin kohdasta Save session for future logins)'
Restarttasi normaalisti

17:05-
VirtualBox Guest Additions 
Virtual Box - Devices, Insert Guest Additions CD image...
se ilmestyi debianin Desktoppiin
Applications, File manageria ja sieltä Devices-kohdassa etsin desktopista kyseisen VBox-GAS_
17:11
Avasin terminator emulatorin ja kirjoitin "cd /media/*/Vbox*
ja sitten ls
sitten kun ollaan oikeassa kansiossa niin sudo bash VBoxLinuxAdditions.run
alkoi tehdä jotain
valittaa, että Kernel headers not found for target kernel 6.1.0-23-amd64 please install them and execute. Desktop on kuitenkoin nyt iso. 
klo 17:20 restarttasin
Otin snapshotin,machine,take a snapshot. Lopetus
17:23 the end

