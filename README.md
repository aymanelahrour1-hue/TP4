# Automatisation des tâches d’administration
**__RIASAT Asad-Ali__**
**__13/02/2026__**

## TP No 4 - Shell et processus

### Introduction :

Ce TP est consacré à l'étude et à la manipulation des processus sous Linux. 
Un processus est une instance d'un programme en cours d'exécution, identifiée par un numéro unique (PID). 
L'objectif est d'apprendre à surveiller l'activité du système, à identifier les ressources consommées et à gérer le cycle de vie des programmes (lancement, arrêt, mise en arrière-plan). 
Nous aborderons également la notion de variables d'environnement qui permettent de configurer le comportement du shell et des applications.

**EXERCICE 1** - Processus

**Objectif :** Utiliser la commande ps pour analyser l'état des processus système et filtrer les informations selon l'utilisateur ou le PID.

**1. Combien de processus sont lancés sur votre système ?**

Pour compter le nombre total de processus, on utilise ps -e (tous les processus) et on compte les lignes avec wc -l.

**Commande :** ps -ef | wc -l
**Sortie :**
```code
toto@p20218:~$ ps -ef | wc -l 215
```
Il ya 215 processus qui sont donc lancé sur notre système.

**2. Quels processus appartiennent à votre utilisateur ?**

On filtre les processus par nom d'utilisateur.

**Commande :** ps -u (nom d'utilisateur)
**Sortie :**
```code
toto@p20218:~$ ps -f -u toto
UID          PID    PPID  C STIME TTY          TIME CMD
toto        6037       1  0 09:04 ?        00:00:00 /lib/systemd/systemd --user
toto        6038    6037  0 09:04 ?        00:00:00 (sd-pam)
toto        6053    6037  0 09:04 ?        00:00:00 /usr/bin/pipewire
toto        6054    6037  0 09:04 ?        00:00:00 /usr/bin/pulseaudio --daemon
toto        6057    6037  0 09:04 ?        00:00:00 /usr/bin/dbus-daemon --sessi
toto        6059       1  0 09:04 ?        00:00:00 /usr/bin/gnome-keyring-daemo
toto        6061    6053  0 09:04 ?        00:00:00 /usr/bin/pipewire-media-sess
toto        6064    6030  0 09:04 ?        00:00:01 xfce4-session
toto        6114    6064  0 09:04 ?        00:00:00 /usr/bin/ssh-agent x-session
toto        6124    6037  0 09:04 ?        00:00:00 /usr/libexec/at-spi-bus-laun
toto        6129    6124  0 09:04 ?        00:00:00 /usr/bin/dbus-daemon --confi
toto        6133    6037  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6139    6037  0 09:04 ?        00:00:00 /usr/libexec/at-spi2-registr
toto        6143    6037  0 09:04 ?        00:00:00 /usr/bin/mate-screensaver --
toto        6147    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfsd
toto        6160    6037  0 09:04 ?        00:00:00 /usr/bin/gpg-agent --supervi
toto        6162    6064  1 09:04 ?        00:00:25 xfwm4 --display :0.0 --sm-cl
toto        6169    6064  0 09:04 ?        00:00:00 xfsettingsd --display :0.0 -
toto        6188    6064  0 09:04 ?        00:00:11 xfce4-panel --display :0.0 -
toto        6192    6064  0 09:04 ?        00:00:03 Thunar --sm-client-id 20babf
toto        6197    6064  0 09:04 ?        00:00:01 xfdesktop --display :0.0 --s
toto        6201    6064  0 09:04 ?        00:00:10 /usr/bin/veyon-server -sessi
toto        6202    6064  0 09:04 ?        00:00:00 xfce4-power-manager --restar
toto        6222    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfs-udisks2-vo
toto        6224    6188  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6225    6188  0 09:04 ?        00:00:01 /usr/lib/x86_64-linux-gnu/xf
toto        6228    6188  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6235    6188  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6238    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfs-afc-volume
toto        6250    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfs-gphoto2-vo
toto        6255    6064  0 09:04 ?        00:00:00 /usr/lib/policykit-1-gnome/p
toto        6256    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfs-mtp-volume
toto        6260    6064  0 09:04 ?        00:00:00 /usr/bin/python3 /usr/share/
toto        6267    6064  0 09:04 ?        00:00:00 light-locker
toto        6273    6201  0 09:04 ?        00:00:00 /usr/bin/veyon-worker {8e997
toto        6275    6064  0 09:04 ?        00:00:00 xiccd
toto        6281    6037  0 09:04 ?        00:00:00 /usr/libexec/dconf-service
toto        6285    6064  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6286    6064  0 09:04 ?        00:00:00 nm-applet
toto        6287    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfs-goa-volume
toto        6288    6188  0 09:04 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xf
toto        6322    6147  0 09:04 ?        00:00:00 /usr/libexec/gvfsd-trash --s
toto        6329    6037  0 09:04 ?        00:00:00 /usr/libexec/gvfsd-metadata
toto        6369       1  0 09:04 ?        00:00:00 /usr/bin/veyon-worker {8e997
toto        6381       1 12 09:04 ?        00:02:53 /usr/bin/x-www-browser
toto        6417    6037  0 09:04 ?        00:00:00 /usr/libexec/xdg-desktop-por
toto        6421    6037  0 09:04 ?        00:00:00 /usr/libexec/xdg-document-po
toto        6424    6037  0 09:04 ?        00:00:00 /usr/libexec/xdg-permission-
toto        6434    6037  0 09:04 ?        00:00:00 /usr/libexec/xdg-desktop-por
toto        6445    6037  0 09:04 ?        00:00:00 /usr/bin/gnome-keyring-daemo
toto        6485    6381  0 09:04 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        6520    6381  0 09:04 ?        00:00:07 /usr/lib/firefox-esr/firefox
toto        6565    6381  0 09:04 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        6659    6381  0 09:04 ?        00:00:13 /usr/lib/firefox-esr/firefox
toto        6688    6381  1 09:04 ?        00:00:16 /usr/lib/firefox-esr/firefox
toto        6945    6381  7 09:09 ?        00:01:23 /usr/lib/firefox-esr/firefox
toto        7028    6381  0 09:10 ?        00:00:02 /usr/lib/firefox-esr/firefox
toto        7058    6381  0 09:10 ?        00:00:07 /usr/lib/firefox-esr/firefox
toto        7062    6381  0 09:10 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        7118    6381  0 09:10 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        7207    6381  1 09:10 ?        00:00:11 /usr/lib/firefox-esr/firefox
toto        7238    6147  0 09:10 ?        00:00:00 /usr/libexec/gvfsd-network -
toto        7254    6147  0 09:10 ?        00:00:00 /usr/libexec/gvfsd-dnssd --s
toto        7287    6381  0 09:11 ?        00:00:03 /usr/lib/firefox-esr/firefox
toto        7329    6381  0 09:11 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        7376    6381  0 09:11 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        7417    6381  0 09:11 ?        00:00:00 /usr/lib/firefox-esr/firefox
toto        7449       1  1 09:12 ?        00:00:17 mousepad /home/toto/README.m
toto        7492       1  0 09:13 ?        00:00:01 engrampa /home/toto/Téléchar
toto        7566       1  0 09:20 ?        00:00:02 xfce4-terminal
toto        7574    7566  0 09:20 pts/0    00:00:00 bash
toto        7623    7574  0 09:27 pts/0    00:00:00 ps -f -u toto
```

Les processus appartenant à l'utilisateur toto sont principalement liés à l'environnement de bureau graphique (XFCE), aux applications ouvertes comme le navigateur Firefox ou l'éditeur Mousepad, ainsi qu'aux instances du shell Bash utilisées pour taper les commandes.

**3- Combien de processus appartiennent à root ?**

Nous allons utiliser la commande précédente avec wc -l pour avoir le nombre de processus appartenant à root.

**Commande :**
```code
ps -f -u root | wc -l
```
**Sortie :**
```code
toto@p20218:~$ ps -f -u root | wc -l
133
```

Il y a 133 processus qui appartiennent donc à root.

**4- Quel est le processus qui a le plus petit PID ?**

Nous allons maintenant analyser les processus en utilisant des outils de surveillance en temps réel et en étudiant la structure hiérarchique du système.

**Commande :** 
```code
ps -ef --sort=pid | head -n 2
```
**Sortie :**
```code
toto@p20218:~$ ps -ef --sort=pid | head -n 2
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 févr.17 ?     00:00:06 /sbin/init
```

Le processus avec le plus petit PID est donc celui-là.
On remarque que son PPID est 0, ce qui signifie qu'il n'a pas de processus parent : c'est le premier processus créé par le noyau (kernel) lors du boot de la machine.

**5- On peut afficher des informations actualis´ees en temps r´eel avec la commande top.
On la quitte en tapant « q ».**

Nous utilisons maintenant l'outil top pour obtenir une vue dynamique de la consommation des ressources.

**Commande :** top

**Sortie :**
```code
top - 09:44:59 up 19:47,  1 user,  load average: 0,75, 0,59, 0,55
Tâches: 219 total,   1 en cours, 218 en veille,   0 arrêté,   0 zombie
%Cpu(s):  1,1 ut,  0,7 sy,  0,0 ni, 98,1 id,  0,1 wa,  0,0 hi,  0,0 si,  0,0 st
MiB Mem :   7758,4 total,   4539,5 libr,   1646,1 util,   1572,8 tamp/cache
MiB Éch :  32768,0 total,  32768,0 libr,      0,0 util.   5289,9 dispo Mem 

    PID UTIL.     PR  NI    VIRT    RES    SHR S  %CPU  %MEM    TEMPS+ COM.     
   5995 root      20   0  973904  90744  58000 S   7,9   1,1   3:15.72 Xorg     
   7566 toto      20   0  389708  38912  30296 S   5,0   0,5   0:06.16 xfce4-t+ 
    893 asterisk -11   0 3294272  77172  36816 S   1,3   1,0  13:59.72 asterisk 
   6162 toto      20   0  691632  77448  58448 S   1,0   1,0   0:49.61 xfwm4    
    628 root      20   0 1504504  54744  29736 S   0,7   0,7   6:09.73 contain+ 
   6201 toto      20   0 1109216  94548  69180 S   0,7   1,2   0:18.89 veyon-s+ 
   6381 toto      20   0 3888672 585192 212636 S   0,7   7,4   5:08.70 x-www-b+ 
     12 root      20   0       0      0      0 I   0,3   0,0   0:06.02 rcu_sch+ 
    531 message+  20   0    9560   5416   3932 S   0,3   0,1   0:15.58 dbus-da+ 
    650 root      20   0   38588   7492   6572 S   0,3   0,1   0:05.61 systemd+ 
   7287 toto      20   0 2670664 155312 105356 S   0,3   2,0   0:06.56 Isolate+ 
   7356 root      20   0       0      0      0 I   0,3   0,0   0:10.40 kworker+ 
   7449 toto      20   0  460540  41112  28920 S   0,3   0,5   0:38.33 mousepad 
   7850 toto      20   0 2420880  87976  75616 S   0,3   1,1   0:00.46 Isolate+ 
   7877 toto      20   0 2417616  80536  66784 S   0,3   1,0   0:01.11 Isolate+ 
   8230 toto      20   0   10404   4068   3292 R   0,3   0,1   0:00.22 top      
      1 root      20   0  164204  10564   7744 S   0,0   0,1   0:06.96 systemd  
```

**Quelle est la mémoire disponible sur votre système ?**

**Observation :** Sur la ligne MiB Mem, on regarde la colonne libr (free).

D'après la capture, la mémoire disponible (libre) est de 4539,5 MiB. Le système dispose au total de 7758,4 MiB, dont une grande partie est encore inutilisée, garantissant une bonne fluidité.

**Quel processus occupe le plus le processeur ?**

**Observation :** On regarde la première ligne du tableau triée par %CPU.

Le processus qui occupe le plus le processeur est Xorg (PID 5995) avec environ 7,9 % du CPU. C'est tout à fait normal car Xorg est le serveur graphique : c'est lui qui gère l'affichage de toutes les fenêtres, les mouvements de la souris et le rendu de l'écran.

**6- Décrire ce qu’affiche la commande pstree.**

La commande pstree affiche les processus sous forme d'arborescence. Elle permet de visualiser graphiquement les liens de parenté (qui est le parent de qui). 
On y voit que tout part de systemd (le tronc) et se divise en branches (services, session utilisateur, terminal, shell).

**Sortie :**
```code
toto@p20218:~$ pstree
systemd─┬─ModemManager───2*[{ModemManager}]
        ├─NetworkManager───2*[{NetworkManager}]
        ├─accounts-daemon───2*[{accounts-daemon}]
        ├─agetty
        ├─apache2───5*[apache2]
        ├─asterisk─┬─astcanary
        │          └─66*[{asterisk}]
        ├─avahi-daemon───avahi-daemon
        ├─colord───2*[{colord}]
        ├─containerd───10*[{containerd}]
        ├─cron
        ├─dbus-daemon
        ├─engrampa───3*[{engrampa}]
        ├─gnome-keyring-d───3*[{gnome-keyring-d}]
        ├─gpm
        ├─libvirtd───18*[{libvirtd}]
        ├─lightdm─┬─Xorg───9*[{Xorg}]
        │         ├─lightdm─┬─xfce4-session─┬─Thunar───2*[{Thunar}]
        │         │         │               ├─applet.py
        │         │         │               ├─light-locker───3*[{light-locker}]
        │         │         │               ├─nm-applet───3*[{nm-applet}]
        │         │         │               ├─polkit-gnome-au───2*[{polkit-gnome-au}]
        │         │         │               ├─ssh-agent
        │         │         │               ├─veyon-server─┬─veyon-worker───8*[{veyon-worker}]
        │         │         │               │              └─11*[{veyon-server}]
        │         │         │               ├─xfce4-notifyd───2*[{xfce4-notifyd}]
        │         │         │               ├─xfce4-panel─┬─panel-10-notifi───2*[{panel-10-notifi}]
        │         │         │               │             ├─panel-14-action───2*[{panel-14-action}]
        │         │         │               │             ├─panel-6-systray───2*[{panel-6-systray}]
        │         │         │               │             ├─panel-8-pulseau───2*[{panel-8-pulseau}]
        │         │         │               │             ├─panel-9-power-m───2*[{panel-9-power-m}]
        │         │         │               │             └─2*[{xfce4-panel}]
        │         │         │               ├─xfce4-power-man───2*[{xfce4-power-man}]
        │         │         │               ├─xfdesktop───2*[{xfdesktop}]
        │         │         │               ├─xfsettingsd───2*[{xfsettingsd}]
        │         │         │               ├─xfwm4───6*[{xfwm4}]
        │         │         │               ├─xiccd───2*[{xiccd}]
        │         │         │               └─2*[{xfce4-session}]
        │         │         └─2*[{lightdm}]
        │         └─2*[{lightdm}]
        ├─mousepad───3*[{mousepad}]
        ├─polkitd───2*[{polkitd}]
        ├─rsyslogd───3*[{rsyslogd}]
        ├─rtkit-daemon───2*[{rtkit-daemon}]
        ├─sshd
        ├─systemd─┬─(sd-pam)
        │         ├─at-spi-bus-laun─┬─dbus-daemon
        │         │                 └─3*[{at-spi-bus-laun}]
        │         ├─at-spi2-registr───2*[{at-spi2-registr}]
        │         ├─dbus-daemon
        │         ├─dconf-service───2*[{dconf-service}]
        │         ├─gnome-keyring-d───2*[{gnome-keyring-d}]
        │         ├─gpg-agent
        │         ├─gvfs-afc-volume───3*[{gvfs-afc-volume}]
        │         ├─gvfs-goa-volume───2*[{gvfs-goa-volume}]
        │         ├─gvfs-gphoto2-vo───2*[{gvfs-gphoto2-vo}]
        │         ├─gvfs-mtp-volume───2*[{gvfs-mtp-volume}]
        │         ├─gvfs-udisks2-vo───3*[{gvfs-udisks2-vo}]
        │         ├─gvfsd─┬─gvfsd-dnssd───2*[{gvfsd-dnssd}]
        │         │       ├─gvfsd-network───3*[{gvfsd-network}]
        │         │       ├─gvfsd-trash───2*[{gvfsd-trash}]
        │         │       └─2*[{gvfsd}]
        │         ├─gvfsd-metadata───2*[{gvfsd-metadata}]
        │         ├─mate-screensave───3*[{mate-screensave}]
        │         ├─pipewire─┬─pipewire-media-───{pipewire-media-}
        │         │          └─{pipewire}
        │         ├─pulseaudio───{pulseaudio}
        │         ├─xdg-desktop-por───5*[{xdg-desktop-por}]
        │         ├─xdg-desktop-por───3*[{xdg-desktop-por}]
        │         ├─xdg-document-po─┬─fusermount
        │         │                 └─5*[{xdg-document-po}]
        │         ├─xdg-permission-───2*[{xdg-permission-}]
        │         └─xfconfd───2*[{xfconfd}]
        ├─systemd-journal
        ├─systemd-logind
        ├─systemd-machine
        ├─systemd-timesyn───{systemd-timesyn}
        ├─systemd-udevd
        ├─udisksd───4*[{udisksd}]
        ├─unattended-upgr───{unattended-upgr}
        ├─upowerd───2*[{upowerd}]
        ├─veyon-service───3*[{veyon-service}]
        ├─veyon-worker───8*[{veyon-worker}]
        ├─wpa_supplicant
        ├─x-www-browser─┬─Isolated Servic───18*[{Isolated Servic}]
        │               ├─3*[Isolated Web Co───22*[{Isolated Web Co}]]
        │               ├─Isolated Web Co───24*[{Isolated Web Co}]
        │               ├─Isolated Web Co───23*[{Isolated Web Co}]
        │               ├─Isolated Web Co───21*[{Isolated Web Co}]
        │               ├─Privileged Cont───21*[{Privileged Cont}]
        │               ├─RDD Process───3*[{RDD Process}]
        │               ├─Socket Process───4*[{Socket Process}]
        │               ├─Utility Process───3*[{Utility Process}]
        │               ├─3*[Web Content───16*[{Web Content}]]
        │               ├─WebExtensions───21*[{WebExtensions}]
        │               └─124*[{x-www-browser}]
        └─xfce4-terminal─┬─bash───pstree
                         └─2*[{xfce4-terminal}]
```

**EXERCICE 2** - Code de statut d’une commande

Nous allons étudier comment les processus indiquent leur succès ou leur échec au système via un code numérique de retour (exit status).

**1- En shell, comment obtenir le statut de la derni`ere commande lancée ?**

**Objectif :** Identifier le résultat (succès ou erreur) de la dernière commande exécutée.

**Commande d’exécution :** echo $?

**Entrées attendues :** Aucune

**Sorties :** Un entier compris entre 0 et 255.

**Tests effectués :**
```code
toto@p20218:~$ ls /etc echo $?
ls: impossible d'accéder à 'echo': Aucun fichier ou dossier de ce type
ls: impossible d'accéder à '2': Aucun fichier ou dossier de ce type
/etc:
adduser.conf            ipp-usb               python3.9
adjtime                 iproute2              qemu-ifdown
alsa                    issue                 qemu-ifup
alternatives            issue.net             radcli
anacrontab              kernel                rc0.d
apache2                 kernel-img.conf       rc1.d
apm                     ldap                  rc2.d
apparmor                ld.so.cache           rc3.d
apparmor.d              ld.so.conf            rc4.d
apt                     ld.so.conf.d          rc5.d
asterisk                libao.conf            rc6.d
avahi                   libaudit.conf         rc.local
bash.bashrc             libblockdev           rcS.d
bash_completion         libibverbs.d          reportbug.conf
bash_completion.d       libnl-3               resolv.conf
bindresvport.blacklist  libpaper.d            rmt
binfmt.d                libreoffice           rpc
ca-certificates         libvirt               rsyslog.conf
ca-certificates.conf    lightdm               rsyslog.d
chatscripts             lighttpd              runit
console-setup           locale.alias          sane.d
containerd              locale.gen            sasl2
cron.d                  localtime             security
cron.daily              logcheck              selinux
cron.hourly             login.defs            sensors3.conf
cron.monthly            logrotate.conf        sensors.d
crontab                 logrotate.d           services
cron.weekly             lvm                   sgml
cups                    machine-id            shadow
cupshelpers             magic                 shadow-
dbus-1                  magic.mime            shells
dconf                   mailcap               skel
debconf.conf            mailcap.order         smi.conf
debian_version          manpath.config        snmp
default                 mate                  sound
deluser.conf            mate-settings-daemon  speech-dispatcher
dhcp                    mdevctl.d             ssh
dictionaries-common     menu                  ssl
discover.conf.d         menu-methods          subgid
discover-modprobe.conf  mime.types            subgid-
docker                  minicom               subuid
dpkg                    mke2fs.conf           subuid-
e2scrub.conf            modprobe.d            sudo.conf
emacs                   modules               sudoers
environment             modules-load.d        sudoers.d
environment.d           motd                  sudo_logsrvd.conf
ethertypes              mtab                  sv
firefox-esr             nanorc                sysctl.conf
fonts                   netconfig             sysctl.d
freetds                 network               systemd
fstab                   NetworkManager        terminfo
fuse.conf               networks              timezone
gai.conf                nftables.conf         timidity
ghostscript             nsswitch.conf         tmpfiles.d
gimp                    openal                ucf.conf
glvnd                   openmpi               udev
gpm.conf                openni2               udisks2
groff                   opt                   ufw
group                   os-release            update-motd.d
group-                  PackageKit            UPower
grub.d                  pam.conf              usb_modeswitch.conf
gshadow                 pam.d                 usb_modeswitch.d
gshadow-                papersize             vbox
gss                     passwd                vdpau_wrapper.cfg
gtk-2.0                 passwd-               veyon
gtk-3.0                 perl                  vim
hddtemp.db              php                   vulkan
host.conf               pipewire              wgetrc
hostname                plymouth              wireshark
hosts                   pm                    wpa_supplicant
hosts.allow             polkit-1              X11
hosts.deny              ppp                   xattr.conf
ifplugd                 profile               xdg
ImageMagick-6           profile.d             xfce4
init.d                  protocols             xml
initramfs-tools         pulse                 xrdb
inputrc                 python3
toto@p20218:~$ echo $?
2
toto@p20218:~$ echo $?
0
toto@p20218:~$ 
```

ls /etc suivi de
```code
echo $?
``` 
-> Affiche 2 et
```code
echo $?
``` 
seul affiche 0.
En shell, on utilise la variable spéciale $? pour obtenir le statut de la dernière commande. La valeur 0 confirme le succès, tandis qu'une valeur supérieure à 0 indique une erreur spécifique.

**2- Comment terminer un script shell avec un code de statut déterminé ?**

**Objectif :** Forcer l'arrêt d'un script en transmettant un code d'état choisi.

**Commande d’exécution :** exit [n] (ex: exit 10)

**Entrées attendues :** Un entier

**Sorties :** Fermeture du processus et transmission du code au processus parent.

exit 10 ferme le terminal.

**3- Quel code renvoie la commande ping vers une machine qui n’existe pas (nom introu-
vable) ?**

**Objectif :** Analyser le code de retour lors d'un échec de PING

**Commande d’exécution :** ping machine.introuvable ; echo $?

**Entrées attendues :** Un nom d'hôte qui n'existe pas.

**Sorties :** Message "Nom ou service inconnu" et code 2.

**Tests effectués :**
```code
toto@p20218:~$ ping toto ; echo $?
ping: toto: Nom ou service inconnu
2
```

La commande ping renvoie le code 2 lorsqu'elle ne parvient pas à trouver l'adresse IP correspondant au nom de la machine demandée.

**4- Quel code renvoie la commande ping vers l’IP d’une machine ´eteinte (request ti-
meout).**

**Objectif :** Analyser le code de retour quand l'IP est valide mais que la cible ne répond pas.

**Commande d’exécution :** 
```code
ping 192.168.1.200 -c 1 ; echo $?
```

**Entrées attendues :** Une adresse IP non attribuée sur le réseau local.

**Sorties :** Message "100% packet loss" et code 1.

**Tests effectués :**
```code
toto@p20218:~$ ping 192.168.52.2 ; echo $?
PING 192.168.52.2 (192.168.52.2) 56(84) bytes of data.
^C
--- 192.168.52.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2037ms

1
```

**EXERCICE 3** - Démarrage et paramétrage des services

Nous allons concevoir un système de surveillance automatisé capable de s'exécuter en arrière-plan dès l'initialisation de la machine.

**1- Créez un script test-reseau.sh qui teste périodiquement (toutes les 60 secondes,
par exemple) et indéfiniment la connexion au réseau en envoyant 2 requˆetes ping `a la
machine www.iutv.univ-paris13.fr. Aprés chaque test, le script devra ajouter à la
fin du fichier /var/log/test-reseau.log un message donnant la date et l’heure du
test ainsi que le résultat du test.** 

**Par exemple :**
```code
samedi 10 sept 2016, 10:19:32 (UTC+0200): test ok (2/2)
samedi 10 sept 2016, 10:20:32 (UTC+0200): test ok (2/2)
samedi 10 sept 2016, 10:21:32 (UTC+0200): test pas ok (1/2)
```

**Objectif :** Développer un script qui vérifie la connectivité toutes les 60 secondes et consigne le résultat.

**Commande d’exécution :** nano ~/test-reseau.sh

**Sorties :** Écritures horodatées dans /var/log/test-reseau.log.

**Tests effectués :**
```code
root@p20218:/home/toto# ./test-reseau.sh &
[1] 2458
root@p20218:/home/toto# more /var/log/test-reseau.log
mercredi 18 févr. 2026, 11:00:50 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:00:55 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:01:56 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:02:57 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:03:58 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:04:59 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:06:00 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:07:01 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:08:02 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:09:03 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:10:04 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:11:05 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:12:06 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:13:07 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:14:07 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:14:08 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:15:08 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:15:09 (CET): test ok (2/2)
```

Le script utilise une boucle infinie et extrait le succès du ping via awk. L'utilisation de >> permet d'ajouter les logs à la suite du fichier sans écraser les précédents.

**2- Créez un service test-reseau qui permette de lancer/arrêter ce script et de tester
s’il est démarré (et, si c’est le cas, d’afficher son identifiant de processus, PID). Par
exemple :**
```code
$ /etc/init.d/test-reseau status
Le service test-reseau est arrete.
$ /etc/init.d/test-reseau start
Service test-reseau demarre.
$ /etc/init.d/test-reseau status
Le service test-reseau est demarre (pid = 5483).
$ /etc/init.d/test-reseau stop
Service test-reseau arrete.
```

**Objectif :** Créer un script de contrôle conforme au standard SysVinit pour piloter le script précédent.

**Commande d’exécution :** sudo nano /etc/init.d/test-reseau

**Tests effectués :**
```code
root@p20218:/home/toto# /etc/init.d/test-reseau start
Service test-reseau démarré (PID 2529)
root@p20218:/home/toto# /etc/init.d/test-reseau status
Le service test-reseau est démarré (pid = 2529).
```

**3- Le système Debian utilise un mécanisme nomm´e ”SysVinit” (remplacé par systemd
dans les nouvelles versions) pour gérer les services, c’est à dire les processus permanents
lancés au démarrage de la machine.**

**A l’aide de la commande ln, faites en sorte que le service test-reseau soit démarré
automatiquement lorsque votre machine d´emarre.**

**Redémarrez la machine et consultez les fichiers /var/log/boot.log
et /var/log/test-reseau.log pour vérifier que le service test-reseau a bien été
démarré. Vérifiez aussi que le processus est bien présent à l’aide de la commande ps.**

Cette étape finale consiste à rendre le service "persistant", c'est-à-dire à faire en sorte qu'il se lance tout seul sans intervention humaine dès que la machine s'allume.

**Objectif :** Créer un lien symbolique pour intégrer le service test-reseau dans la séquence de démarrage du système (Runlevel 5).

**Commande d’exécution :**
```code
ln -s /etc/init.d/test-reseau /etc/rc5.d/S01test-reseau
```
**Entrées attendues :** Le script de service doit être présent dans /etc/init.d/ et posséder les droits d'exécution.
**Sorties :** Création d'un lien symbolique nommé S01test-reseau dans le répertoire /etc/rc5.d/. Le "S" signifie Start et "01" indique l'ordre de priorité au démarrage.

**Tests effectués :**
```code
root@p20218:/home/toto# ln -s /etc/init.d/test-reseau /etc/rc5.d/S01test-reseau
ln: impossible de créer le lien symbolique '/etc/rc5.d/S01test-reseau': Le fichier existe
root@p20218:/home/toto# reboot
```
Après redémarrage nous vérifions si le processus est vivant et si il a recommencé à écrire :
```code
root@p20218:/home/toto# ps -ef | grep test-reseau.sh
root        2458    2444  0 11:35 pts/0    00:00:00 /bin/bash ./test-reseau.sh
root        2529       1  0 11:38 pts/0    00:00:00 bash /home/toto/test-reseau.sh
root        3052    2444  0 11:46 pts/0    00:00:00 grep test-reseau.sh
root@p20218:/home/toto# tail /var/log/test-reseau.log
mercredi 18 févr. 2026, 11:41:31 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:41:45 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:42:32 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:42:46 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:43:33 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:43:47 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:44:34 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:44:48 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:45:35 (CET): test ok (2/2)
mercredi 18 févr. 2026, 11:45:49 (CET): test ok (2/2)
root@p20218:/home/toto# 
```

## Conclusion :
Pour conclure ce TP4, on a vraiment plongé dans les coulisses de Linux. On a commencé par observer la vie des processus (leur naissance avec le PID 1, leur hiérarchie et leur consommation de ressources), pour finir par créer notre propre service automatisé.
Le plus important à retenir, c'est que sous Linux, rien n'est "magique" : chaque application, du simple ping au navigateur, est un processus qui communique avec le système via des codes de statut et des signaux. Savoir manipuler ces processus et automatiser un script de surveillance via init.d, c'est passer du rôle de simple utilisateur à celui d'administrateur capable de dompter sa machine.
