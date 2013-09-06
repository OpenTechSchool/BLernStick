BerlinLernStick
===============

A mobile and secure Learn- and Working-Environment for IT-Labs Berlin (IT-Schülerlabore), school and home.

The project is funded by TSB Technologiestiftung Berlin.

www.tsb-berlin.de

www.itlabsberlin.de

Howto
-----

Per Pinning festlegen, dass der Bankix-Kernel immer genutzt wird

    vim /etc/apt/preferences

    Package: linux-image* linux-headers*
    Pin: origin www.heise.de
    Pin-Priority: 1001

Paketquelle von heise.de eintragen

    echo "deb http://www.heise.de/ct/projekte/ctbankix precise main" > /etc/apt/sources.list.d/ctbankix.list

Paketquellen aktualisieren (eine GPG-Warnung ist hier normal)

    apt-get update

Schlüssel für heise-Paketquellen holen und eintragen

    apt-get install ctbankix-keyring

Paketquellen aktualisieren

    apt-get update

*HACK:* Fehler mit grub-probe unter Ubuntu-Livesystemen reparieren

    mv /usr/sbin/grub-probe /usr/sbin/grub-probe.orig
    wget http://cdn.edoceo.com/bin/grub-probe.sh -O /usr/sbin/grub-probe
    chmod +x /usr/sbin/grub-probe

Bankix-Kernel installieren (Version ist herauszufinden über `grep ^Package: /var/lib/apt/lists/www.heise.de_*_Packages`)

    apt-get install linux-image-3.?.???

alten Kernel deinstallieren (Version ist herauszufinden über `dpkg -l | grep linux-image-`)

    apt-get remove linux-image-3.?.???

Kernelabhängigkeiten unterbinden

    apt-get remove linux-image-generic-pae
    apt-get remove linux-headers-generic-pae
