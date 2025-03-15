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
* **Vertraulichkeit**: Nachrichten können von dritten nicht gelesen werden
* **Integrity**: Nachrichten sind unverändert 
*  **Authenticity**: Zugriff auf die Nachrichten wird durch den Schlüssel autorisiert
 
Programme für die Verwendung von symmetrischer Verschlüsselung:
* GNU Privacy Guard
* OpenSSL Project