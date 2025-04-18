# 🛡️ Identity and Access Management

## 📘 Einführung

Wie identifizieren wir Benutzer? Wie beweisen sie ihre Identität? Wie verhindern wir Missbrauch? Dieses Modul führt durch die Konzepte rund um **Identifikation, Authentifizierung, Autorisierung** und **Accountability**.

### 🎯 Lernziele

| Thema | Beschreibung |
|-------|--------------|
| IAAA | Vier Grundpfeiler: Identification, Authentication, Authorisation, Accountability |
| MFA | Multi-Faktor-Authentifizierung verstehen und anwenden |
| Zugriff | Access Control Models wie DAC, RBAC, MAC |
| Logging | Verantwortung durch Protokollierung (SIEM) |
| SSO | Single Sign-On verstehen und nutzen |

---

## 🔐 IAAA – Grundpfeiler der Zugriffssicherheit

| Prozess | Beschreibung |
|---------|-------------|
| **Identification** | Wer ist der Benutzer? (z. B. Benutzername oder E-Mail) |
| **Authentication** | Ist er wirklich, wer er vorgibt zu sein? (z. B. Passwort) |
| **Authorisation** | Was darf der Benutzer tun? |
| **Accountability** | Wer hat was wann gemacht? (z. B. durch Logging) |

---

## 🧍 Identification

- Benutzer beansprucht eine eindeutige Identität
- Z. B. Benutzername, E-Mail, Studentennummer, Telefonnummer

---

## ✅ Authentication

- Bestätigung der behaupteten Identität
- Drei Hauptarten:

| Methode | Beispiel |
|--------|---------|
| **Etwas, das du weißt** | Passwort, PIN, Passphrase |
| **Etwas, das du hast** | Sicherheits-Token, Handy, SMS-Code |
| **Etwas, das du bist** | Fingerabdruck, Gesichtserkennung |

### 🔐 Multi-Factor Authentication (MFA)

- Kombination aus zwei oder mehr Authentifizierungsmechanismen
- Beispiel: Bankkarte + PIN = 2FA

---

## 🚪 Authorisation & Access Control

| Begriff | Beschreibung |
|---------|-------------|
| **Authorisation** | Welche Ressourcen darf der Benutzer verwenden? |
| **Access Control** | Technische Durchsetzung dieser Regeln |

Beispiel: Zugriff auf eigene E-Mails, aber nicht auf die der Kollegen.

---

## 📊 Accountability & Logging

- Nutzeraktivitäten nachvollziehbar machen
- Logging als Grundlage für:

  - Audits & Compliance
  - Incident Response
  - Forensik
  - Alarme bei Anomalien

### SIEM – Security Information and Event Management

- Zentralisierte Analyse und Korrelation von Logdaten

---

## 🧾 Identity vs. Access Management

| Begriff | Fokus |
|--------|-------|
| **IdM** | Verwaltung von Identitäten, Authentifizierung & Autorisierung |
| **IAM** | Ganzheitliches Konzept inkl. Access Governance, SSO, MFA |

---

## 🧨 Angriffe auf Authentifizierung

- Replay-Attacken bei einfacher Verschlüsselung
- Lösung: **Einmalige Tokens**, **Zeitsynchronisierung**, etablierte Protokolle

---

## 🧷 Access Control Models

| Modell | Beschreibung |
|--------|-------------|
| **DAC** | Ressourcenbesitzer entscheidet über Zugriffsrechte |
| **RBAC** | Zugriff basiert auf Benutzerrolle |
| **MAC** | Strikte Regeln, vor allem für hochsichere Systeme |

Beispiele: AppArmor, SELinux

---

## 🔑 Single Sign-On (SSO)

- Einmal anmelden, auf mehrere Dienste zugreifen
- Vorteile:

  - Ein starkes Passwort merken
  - Zentrale MFA-Verwaltung
  - Einfachere Passwortverwaltung
  - Effizienter Zugriff für Nutzer

---

## 📚 Fazit

| Bereich | Rolle |
|--------|-------|
| Identifikation & Authentifizierung | Wer bist du? Bist du es wirklich? |
| Autorisierung & Kontrolle | Was darfst du tun? |
| Logging & Accountability | Was hast du getan? |
| IAM & SSO | Verwaltung & Vereinfachung des sicheren Zugriffs |