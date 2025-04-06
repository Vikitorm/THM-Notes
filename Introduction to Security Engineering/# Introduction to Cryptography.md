# Introduction to Cryptography

### Terminology
| Begriff | Beschreibung|
| --------| -------------|
| Kryptografischer Algorithmus | Bestimmt den Prozess der Verschlüsselung / Entschlüsselung |
| Key | Wird von dem Algorithmus benötigt, um nach einem bestimmten Schema zu Verschlüsseln |
| Plaintext | Normaler unverschlüsselter Text |
| Ciphertext | Verschlüsselter Text |

## Symmetric Encryption
Bei der symmetrischen Verschlüsselung wird **Plaintext** mit Hilfe eines **Keys** zu einem **Ciphertext**.
Empfänger können mit demselben **Key** und **Ciphertext**, den **Plaintext** entschlüsseln.

Symmetrische Verschlüsselung erreicht folgende Ziele:
* **Confidentiality**: Nachrichten können von dritten nicht gelesen werden
* **Integrity**: Nachrichten sind unverändert 
*  **Authenticity**: Zugriff auf die Nachrichten wird durch den Schlüssel autorisiert
 
Programme für die Verwendung von symmetrischer Verschlüsselung:
* GNU Privacy Guard
* OpenSSL Project

gpg --symmetric --cipher-algo CIPHER message.txt
* Verschlüsselt eine Datei
  
gpg --output original_message.txt --decrypt message.gpg
* Entschlüsselt eine Datei

openssl aes-256-cbc -e -in message.txt -out encrypted_message
* Verschlüsselt eine Datei

openssl aes-256-cbc -d -in encrypted_message -out original_message.txt
* Entsachlüsselt eine Datei

openssl aes-256-cbc -pbkdf2 -iter 10000 -e -in message.txt -out encrypted_message
* -pbkdf2 & -iter 10000: Machen die Verschlüsselung stark gegen Brute-Force Angriffe

openssl aes-256-cbc -pbkdf2 -iter 10000 -d -in encrypted_message -out original_message.txt
* Stärkere entschlüsselung

## Asymmetrische Verschlüsselung
* Ein Schlüsselpaar von öffentlichem-/privatem Schlüssel wird generiert
* **Öffentlicher Schlüssel**: Kann mit anderen geteilt werden, um die Nachricht zu verschlüsseln (Integrity)
* **Privater Schlüssel**: Wird mit niemanden geteilt, wird verwedet, um die Nachricht zu entschlüsseln
* Öffentliche Schlüssel müssen für eine Einwandfreie Kommunikation ausgetauscht werden!
* Die originalität des Privaten Schlüssels kann getestet werden, indem man mit dem privaten Schüssel eine Nachricht verschlüsselt und andere Teilnehmer diese mit dem zugehöregen Öffentlichen Schlüssel versuchen zu entschlüsseln

RSA
* Name basiert auf den Namen der Entwickler dieser Technologie
* Kann für die asymmetrische Verschlüsselung verwendet werden
* (2 Primahlen p, q & 2 Integer Zahlen e, d müssen hierfür definiert werden)
  * Basiert auf den Fakt, dass Faktorisierungen schwer zu berechnen sind
  * P & q sollten sehr große Zahlen sein
  * Wenn ein Angreifer p & q raten kann, sind die generierten Schlüssel unsicher

openssl genrsa -out private-key.pem 2048
* Generiert eine 2048 Bit Private Key

openssl rsa -in private-key.pem -pubout -out public-key.pem
* Leitet aus dem privaten Schlüssel einen öffentlichen Schlüssel

openssl rsa -in private-key.pem -text -noout
* Gibt die Variablen des privaten Schlüssels preis

openssl pkeyutl -encrypt -in plaintext.txt -out ciphertext -inkey public-key.pem -pubin
* Verschlüsselung mit dem öffentlichen Schlüssel

openssl pkeyutl -decrypt -in ciphertext -inkey private-key.pem -out decrypted.txt
* Entschlüsselung mit dem privaten Schlüssel

## Diffie-Hellman Key Exchange
* Asymmetrischer Verschlüsselungs Algorithmus
* Erlaubt den austausch von privaten Schlüsseln zur Sicheren Kommunikation
  *  Beide Parteien einigen sich auf den Key
*  Dieser Algorithmus kann in einer "Man-in-the-middel" Attacke angegriffen werden

openssl dhparam -in dhparams.pem -text -noout
* Zeigt die Parameter des Diffie-Hellman Keys an

## Hashing
* Funktion, welche eine größe Menge an Daten nimmt und einen Fixen Wert (Format) zurückgibt

sha256sum <Datei>
* Bildet aus einer Datei einen sha256-Hash
* Viele Datenbanken speichern Passwort-Hashes statt klare Passwörter
* Zur wahrung der Integrität kann mit hashing festgestellt werden, ob eine Datei Modifikationen erhalten hat
* Einige Hash-Funktionen wie SHA1 oder MD5 sind gebrochen, mit ihnen sollte nichts mehr auf die Integrität überprüft werden, da diese Hash-Kollisionen haben
  * Dementsprechen kann eine Datei denselben Hash haben und zugleich einen anderen Inhalt haben

HMAC (Hash-based message authentication)
* Schlüssel-Hash-Nachrichtenauthentifizierungscode
  * Basiert auf eine Privaten Schlüssel & einer Hash-Funktion, ipad & opad

hmac256 s!Kr37 message.txt
* Bestimmten den HMAC für die Datei message.txt mit dem Schlüssel s!Kr37

## PKI and SSL/TLS
* EIn Angreifer kann ja zweischen 2 Parteien bei Diffie-Hellman sein und die Kommunikation trotz dme Glaube der Sicherheit einsehen & verändern
* Hier kommt PKI: Websites bestätigen ihre Identität mit einem Ausgestellten Zertifikat
* Für die Signierung eines Zertifikats wird benötigt:
  * CSR (Certificate Signing Request): Ein Zertifikat generieren
  * Der öffentliche Schlüssel von einer CA signieren lassen
    * Self-signing wird als unsicher betrachtet

openssl req -new -nodes -newkey rsa:4096 -keyout key.pem -out cert.csr
* Generiert eine neue CSR
  * req -new create a new certificate signing request
  * -nodes save private key without a passphrase
  * -newkey generate a new private key
  * rsa:4096 generate an RSA key of size 4096 bits
  * -keyout specify where to save the key
  * -out save the certificate signing request

openssl req -x509 -newkey -nodes rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365
* Generiert ein selbst signiertes Zertifikat (Nicht empfohlen)

openssl x509 -in cert.pem -text
* Inspizieren von einem Zertifikat

## Authenticating with Passwords
* Username + Password: UNsichere Datenbank
* Username + Hash(Password): Schon besser
* Username + Hash(Password+Salt) + Salt: MEGA, es geht auch "hash(hash(password) + salt)"

## Cryptography and Data - Example
* Client requests server’s SSL/TLS certificate
* Server sends SSL/TLS certificate to the client
* Client confirms that the certificate is valid
* Wenn der Aussteller des Zertifikates bekannt ist, wird mit dem öffentlichem Schlüssel der verschlüsselte Hash entschlüsselt & mit dem Hash des Zertifikates verglichen
* Sobal dieser Abgleich zutrifft, wird eine SSL/TLS initiiert
  * Von da an wird jegliche Kommunikation verschlüsselt sein 