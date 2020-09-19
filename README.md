# SRTDecoder (Raspberry Pi Hardware H.264/AAC Live Decoder für SRT)

Konfiguration für Raspis zum Abrufen und Decodieren von SRT Signalen.

## Features
- Stream Clock Recovery on HDMI output
- Interlaced Decoding and Output
- Auto Reconnection
- Decoded Video Output only (No system messages on screen)
- Up to 1080p50

## Empfohlene Hardware

-   Raspberry Pi 3B
-   BMD UpDownCross HD (für Reclocking / Signalwandlung)

## Installation

`Raspberry Pi OS (32-bit) Lite` oder `Raspberry Pi OS (32-bit) with desktop` installieren.

SRTDecoder samt Abhängigkeiten installieren:
```
sudo apt-get update && \
sudo apt-get -y upgrade && \
sudo apt-get -y install omxplayer ntp git tclsh pkg-config cmake libssl-dev build-essential && \
git clone https://github.com/OKTV-RLP/srtdecoder.git && \
sudo \cp -rf srtdecoder/* / && \
sudo rm -rf srtdecoder && \
wget https://github.com/Haivision/srt/archive/v1.4.1.tar.gz && \
sudo tar -zxvf v1.4.1.tar.gz -C /usr/local && \
rm -rf v1.4.1.tar.gz && \
cd /usr/local/srt-1.4.1 && \
sudo ./configure && \
sudo make && \
sudo make install && \
cd && \
sudo stream-config
```


## Nutzung

- Automatischer Start des Diensts aktivieren mit `sudo stream enable`
- Automatischer Start des Diensts deaktivieren mit `sudo stream disable`
- Einstellung für automatischen Start anzeigen mit `sudo stream check`
- Dienst starten mit `sudo stream start`
- Dienst stoppen mit `sudo stream stop`
- Dienst neustarten mit `sudo stream restart`
- Status des Dienstes abrufen mit `sudo stream`
- Konfiguration mit `sudo stream-config`

Wenn kein Signal anliegt startet der Prozess andauernd neu. Ebenso falls der Prozess wegen irgendeinem Fehler während des Streams mal terminieren sollte. Nach wenigen Sekunden sollte es dann weiter gehen.
Der leere Hintergrund (blank) ist absichtlich leicht grau, damit man sieht, dass das System ein Signal ausgibt bzw. ob der omxplayer selbst läuft.


## ToDo

- [ ] Web-GUI