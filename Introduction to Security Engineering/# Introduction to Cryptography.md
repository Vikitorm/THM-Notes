# 🪐 Einführung in die Kryptographie

## 🔑 Terminologie

| Begriff                    | Beschreibung                                                                 |
|---------------------------|------------------------------------------------------------------------------|
| **Kryptografischer Algorithmus** | Bestimmt den Prozess der Verschlüsselung / Entschlüsselung                |
| **Key (Schlüssel)**              | Wird vom Algorithmus benötigt, um nach einem bestimmten Schema zu verschlüsseln |
| **Plaintext**                   | Normaler, unverschlüsselter Text                                          |
| **Ciphertext**                  | Verschlüsselter Text                                                     |

---

## 🔒 Symmetrische Verschlüsselung

- Der **Plaintext** wird mit einem **Key** in **Ciphertext** umgewandelt.
- Empfänger können mit demselben **Key** und dem **Ciphertext** den ursprünglichen **Plaintext** entschlüsseln.

### 🎯 Ziele

- **Confidentiality**: Nachrichten können von Dritten nicht gelesen werden  
- **Integrity**: Nachrichten bleiben unverändert  
- **Authenticity**: Der Zugriff wird durch den Schlüssel autorisiert  

### 🛠 Tools

- **GNU Privacy Guard (gpg)**
- **OpenSSL**

```bash
# Mit gpg verschlüsseln und entschlüsseln
gpg --symmetric --cipher-algo CIPHER message.txt
gpg --output original_message.txt --decrypt message.gpg

# Mit OpenSSL verschlüsseln und entschlüsseln
openssl aes-256-cbc -e -in message.txt -out encrypted_message
openssl aes-256-cbc -d -in encrypted_message -out original_message.txt

# Stärkere Verschlüsselung mit PBKDF2
openssl aes-256-cbc -pbkdf2 -iter 10000 -e -in message.txt -out encrypted_message
openssl aes-256-cbc -pbkdf2 -iter 10000 -d -in encrypted_message -out original_message.txt
```

---

## 🔐 Asymmetrische Verschlüsselung

- Es wird ein **Schlüsselpaar** aus **öffentlichem** und **privatem** Schlüssel generiert.
- Der **öffentliche Schlüssel**:
  - Kann weitergegeben werden
  - Wird zur **Verschlüsselung** verwendet
- Der **private Schlüssel**:
  - Bleibt geheim
  - Wird zur **Entschlüsselung** verwendet
- 🔁 **Test der Echtheit**:
  - Eine Nachricht wird mit dem privaten Schlüssel verschlüsselt
  - Andere Teilnehmer versuchen, sie mit dem öffentlichen Schlüssel zu entschlüsseln

### 🔢 RSA (Rivest-Shamir-Adleman)

- Basiert auf der Schwierigkeit der Faktorisierung großer Zahlen
- Benötigt:
  - Zwei große Primzahlen: `p`, `q`
  - Zwei Integer-Zahlen: `e`, `d`

```bash
# RSA-Schlüsselpaar generieren
openssl genrsa -out private-key.pem 2048

# Öffentlichen Schlüssel aus privatem erzeugen
openssl rsa -in private-key.pem -pubout -out public-key.pem

# Private-Key-Inhalte anzeigen
openssl rsa -in private-key.pem -text -noout

# Datei mit öffentlichem Schlüssel verschlüsseln
openssl pkeyutl -encrypt -in plaintext.txt -out ciphertext -inkey public-key.pem -pubin

# Datei mit privatem Schlüssel entschlüsseln
openssl pkeyutl -decrypt -in ciphertext -inkey private-key.pem -out decrypted.txt
```

---

## 🔄 Diffie-Hellman Schlüsselaustausch

- Asymmetrischer Algorithmus zum sicheren Austausch eines gemeinsamen Schlüssels
- Beide Parteien einigen sich auf einen gemeinsamen Schlüssel
- ⚠️ **Verwundbar gegenüber Man-in-the-Middle-Angriffen**

```bash
# Parameter anzeigen
openssl dhparam -in dhparams.pem -text -noout
```

---

## 🧮 Hashing

- Eine Hash-Funktion erzeugt aus beliebigen Daten einen **fixen Wert** (Hash)

```bash
# SHA-256 Hash erzeugen
sha256sum <Datei>
```

### 🔍 Verwendung

- Passwörter werden als Hash gespeichert, nicht im Klartext.
- Hashes prüfen die **Integrität** von Dateien.

> ⚠️ Veraltete Hash-Funktionen wie SHA1 und MD5 sind unsicher (Hash-Kollisionen möglich)

### 🔐 HMAC (Hash-based Message Authentication Code)

- Basiert auf einem **privaten Schlüssel**, einer **Hash-Funktion**, sowie `ipad` und `opad`

```bash
# HMAC berechnen
hmac256 s!Kr37 message.txt
```

---

## 🛡️ PKI und SSL/TLS

- PKI schützt vor *Man-in-the-Middle*-Angriffen beim Schlüsselaustausch
- **Websites verwenden digitale Zertifikate**, um ihre Identität zu bestätigen

### 🔧 Zertifikate erstellen & inspizieren

```bash
# CSR (Certificate Signing Request) erzeugen
openssl req -new -nodes -newkey rsa:4096 -keyout key.pem -out cert.csr

# Selbst signiertes Zertifikat (nicht empfohlen)
openssl req -x509 -newkey -nodes rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365

# Zertifikat inspizieren
openssl x509 -in cert.pem -text
```

---

## 🔐 Authentifizierung mit Passwörtern

| Methode                            | Sicherheit     |
|------------------------------------|----------------|
| Username + Passwort                | ❌ Unsicher    |
| Username + `Hash(Passwort)`        | ✔️ Besser      |
| Username + `Hash(Passwort + Salt)` | ✅ Sehr gut     |
| `Hash(Hash(Passwort) + Salt)`      | ✅✅ Noch besser |

---

## 🔁 Beispiel: Kryptografie im Datenfluss

1. Client fordert das SSL/TLS-Zertifikat vom Server an  
2. Server sendet Zertifikat zurück  
3. Client prüft, ob das Zertifikat gültig ist:  
   - Ist der Aussteller bekannt?  
   - Hash stimmt mit Signatur überein?  
4. SSL/TLS-Verbindung wird aufgebaut  
   → Kommunikation ab diesem Punkt ist **verschlüsselt**