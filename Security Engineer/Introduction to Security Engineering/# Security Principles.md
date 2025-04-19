# 🛡️ Sicherheitsprinzipien

## 📘 Einführung

Sicherheit ist ein zentrales Thema – doch was bedeutet sie wirklich? Diese Lektion beleuchtet grundlegende Sicherheitsprinzipien, Modelle und Frameworks.

### 🎯 Lernziele

| Thema | Beschreibung |
|-------|--------------|
| CIA | Vertraulichkeit, Integrität, Verfügbarkeit |
| DAD | Gegenspieler: Offenlegung, Veränderung, Zerstörung |
| Modelle | Bell-LaPadula, Biba, Clark-Wilson |
| Konzepte | Zero Trust, Verteidigung in der Tiefe, Parkerian Hexad |
| Standards | ISO/IEC 19249 |

---

## 🔐 Das CIA-Triad

| Prinzip | Beschreibung |
|---------|--------------|
| **Confidentiality** | Nur autorisierte Personen haben Zugriff auf Daten |
| **Integrity** | Daten dürfen nicht unbemerkt verändert werden |
| **Availability** | Systeme müssen verfügbar sein, wenn sie gebraucht werden |

Beispiele: Online-Shopping, Patientendaten im Gesundheitswesen.

---

## 🔍 Erweiterungen von CIA

| Begriff | Bedeutung |
|---------|-----------|
| **Authenticity** | Daten stammen wirklich von der behaupteten Quelle |
| **Nonrepudiation** | Absender kann Ursprung nicht abstreiten |

---

## 🧮 Parkerian Hexad

| Element | Beschreibung |
|---------|-------------|
| Availability | Verfügbarkeit |
| Utility | Nutzbarkeit der Daten |
| Integrity | Unverändertheit |
| Authenticity | Echtheit |
| Confidentiality | Vertraulichkeit |
| Possession | Kontrolle/Besitz über Daten |

---

## ☠️ DAD – Angriffsmodell

| Prinzip | Gegenteil von |
|---------|---------------|
| **Disclosure** | → Confidentiality |
| **Alteration** | → Integrity |
| **Destruction/Denial** | → Availability |

Diese drei Angriffsformen bedrohen Systeme. Schutzmechanismen müssen darauf abgestimmt sein.

---

## 🧱 Sicherheitsmodelle

### 🔒 Bell-LaPadula (Vertraulichkeit)

| Regel | Bedeutung |
|-------|-----------|
| No read up | Untere dürfen nicht nach oben lesen |
| No write down | Obere dürfen nicht nach unten schreiben |

### 🛡️ Biba (Integrität)

| Regel | Bedeutung |
|-------|-----------|
| No read down | Obere dürfen nicht von unteren lesen |
| No write up | Untere dürfen nicht nach oben schreiben |

### ⚙️ Clark-Wilson (Prozessorientiert)

- **CDI**: Zu schützende Daten
- **UDI**: Eingaben / nicht vertrauenswürdige Daten
- **TP**: Aktionen, die CDIs verändern dürfen
- **IVP**: Prüfungen auf Datenkonsistenz

---

## 🧩 Weitere Modelle

- Brewer-Nash
- Goguen-Meseguer
- Sutherland
- Graham-Denning
- Harrison-Ruzzo-Ullman

---

## 🧱 Defense-in-Depth

Mehrstufige Sicherheit: wie bei einem Safe in einem Gebäude mit mehreren Schlüsseln und Kameras.

---

## 🌐 ISO/IEC 19249 – Architekturprinzipien

| Prinzip | Beschreibung |
|---------|--------------|
| **Domain Separation** | Trennung nach Zuständigkeit und Zugriffen |
| **Layering** | Schutz auf mehreren Abstraktionsebenen (z. B. OSI-Modell) |
| **Encapsulation** | Daten nur über definierte Schnittstellen zugänglich |
| **Redundancy** | Verfügbarkeit und Integrität durch Backup & Duplikation |
| **Virtualization** | Sandboxen und Isolierung durch virtuelle Umgebungen |

### 🛠️ Designprinzipien nach ISO

1. **Least Privilege**
2. **Attack Surface Minimisation**
3. **Centralized Parameter Validation**
4. **Centralized General Security Services**
5. **Preparing for Error and Exception Handling**

---

## 🔁 Zero Trust vs. Trust but Verify

| Prinzip | Beschreibung |
|---------|-------------|
| **Trust but Verify** | Vertrauen, aber kontrollieren (z. B. durch Logs) |
| **Zero Trust** | „Vertraue nie, überprüfe immer“ – auch intern! |

➡️ Umsetzung z. B. durch Microsegmentation & ACLs

---

## ⚠️ Vulnerability, Threat, Risk

| Begriff | Bedeutung |
|---------|-----------|
| **Vulnerability** | Schwachstelle im System |
| **Threat** | Möglicher Angreifer oder Angriff |
| **Risk** | Wahrscheinlichkeit × Auswirkung des Angriffs |

Beispiel: Verwundbare Datenbank mit öffentlichem Exploit = **hohes Risiko**.

---

## 📚 Fazit

- CIA und DAD sind grundlegende Denkmodelle
- Sicherheitsmodelle helfen, Prinzipien strukturiert umzusetzen
- ISO/IEC 19249 liefert Architektur- und Designprinzipien
- Zero Trust ist modernes Sicherheitsparadigma
- Risiken ergeben sich aus dem Zusammenspiel von Schwachstelle & Bedrohung