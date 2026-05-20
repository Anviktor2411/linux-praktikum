# Linux Praktikum — Debian VM

Debian virtuaalmasina seadistamine ja põhikäskude praktikum. Kooli IT-praktikum.

## Keskkond

- **OS**: Debian 12 (Bookworm)
- **Virtualisatsioon**: VMware / VirtualBox
- **Ühendus**: SSH

## Kaetud teemad

- Failisüsteemi navigeerimine
- Kasutajate ja õiguste haldus
- Võrgu konfiguratsioon
- Failide edastamine SCP kaudu
- Teenuste haldus systemctl-ga

## Põhikäsud

### Failisüsteem

```bash
ls -la          # failide nimekiri koos õigustega
cd /etc         # kataloogi vahetus
pwd             # praegune asukoht
mkdir projekt   # uus kataloog
rm -rf kataloog # kataloogi kustutamine
cp fail1 fail2  # kopeerimine
mv fail1 fail2  # teisaldamine / ümbernimetamine
```

### Kasutajad ja õigused

```bash
sudo useradd -m kasutaja        # uus kasutaja
sudo passwd kasutaja            # parooli seadmine
sudo usermod -aG sudo kasutaja  # sudo õigused
chmod 755 fail                  # õiguste muutmine
chown kasutaja:grupp fail       # omaniku muutmine
```

### Võrk

```bash
ip a                    # IP aadressid
ip route                # marsruutimistabel
ping 8.8.8.8            # ühenduse test
ss -tulnp               # avatud pordid
```

### Failide edastamine SCP-ga

```bash
# Faili saatmine teisele masinale
scp fail.txt kasutaja@192.168.1.100:/home/kasutaja/

# Faili toomine teiselt masinalt
scp kasutaja@192.168.1.100:/home/kasutaja/fail.txt .

# Kataloogi edastamine
scp -r kataloog/ kasutaja@192.168.1.100:/sihtkoht/
```

### Teenuste haldus

```bash
sudo systemctl start teenus     # käivita
sudo systemctl stop teenus      # peata
sudo systemctl restart teenus   # taaskäivita
sudo systemctl enable teenus    # käivita automaatselt
sudo systemctl status teenus    # vaata olekut
```

### Logid

```bash
journalctl -u teenus            # teenuse logid
tail -f /var/log/syslog         # reaalajas logid
grep "error" /var/log/syslog    # otsi logidest
```

## Pakettide haldus (APT)

```bash
sudo apt update                 # uuenda paketinimekiri
sudo apt upgrade                # uuenda paketid
sudo apt install pakett         # installi
sudo apt remove pakett          # eemalda
sudo apt search märksõna        # otsi pakette
```

## Õpitud

- Debian Linuxi põhikäsud ja failisüsteem
- SSH kaudu serveri haldamine
- SCP failiedastus võrgus
- Süsteemiteenuste haldus systemctl-ga
- APT paketihaldur
