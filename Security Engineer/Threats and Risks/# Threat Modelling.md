# 🛡️ Threat Modelling

## 📘 Einführung

Threat Modelling ist ein strukturierter Prozess zur Identifikation, Bewertung und Priorisierung von Sicherheitsrisiken. Es hilft Organisationen, Angriffsflächen zu reduzieren und Sicherheitsmaßnahmen gezielt zu platzieren.

### 🎯 Lernziele

| Thema | Beschreibung |
|-------|--------------|
| Grundlagen | Bedeutung und Nutzen von Threat Modelling |
| Prozesse | Schrittweise Vorgehensweise |
| Teams | Beteiligte Rollen |
| Frameworks | STRIDE, DREAD, PASTA, MITRE ATT&CK |
| Tools | ATT&CK Navigator und andere Anwendungen |

---

## 🧠 Grundlagen

| Begriff | Beschreibung |
|--------|--------------|
| **Threat** | Möglicher Angriff oder schädliches Ereignis |
| **Vulnerability** | Schwachstelle, die ausnutzbar ist |
| **Risk** | Wahrscheinlichkeit × Auswirkung eines Angriffs |

🔐 Analogie: Haus mit offenem Fenster = hohe Einbruchsgefahr

---

## 🧭 Prozess des Threat Modellings

1. **Scope definieren**
2. **Assets identifizieren**
3. **Bedrohungen ermitteln**
4. **Risiken analysieren & priorisieren**
5. **Gegenmaßnahmen implementieren**
6. **Ergebnisse evaluieren & überwachen**

---

## 👥 Beteiligte Teams

| Team | Rolle |
|------|-------|
| Security Team | Fachliche Leitung, Risikoanalyse |
| Dev Team | Implementierung sicherer Anwendungen |
| IT/Ops | Infrastrukturwissen |
| GRC Team | Regulatorische Anforderungen |
| Stakeholder | Kritische Assets & Business Impact |
| Endnutzer | Praktische Perspektive und Verhalten |

---

## 🌳 Attack Trees

- Ziel-orientierte Diagramme
- Visualisieren Wege & Bedingungen für Angriffe
- Ergänzung durch **Attack Paths** möglich

---

## 🧩 MITRE ATT&CK Framework

| Element | Beschreibung |
|---------|--------------|
| **Tactics** | Was will der Angreifer erreichen? |
| **Techniques** | Wie wird das Ziel erreicht? |
| **Mitigations** | Gegenmaßnahmen |
| **Detections** | Erkennungsansätze |

🧭 **ATT&CK Navigator** als Mapping-Tool nutzbar.

### Anwendung im Modellierungsprozess:

- Bedrohungen zu ATT&CK-Techniken mappen
- Beispiele & reale Angriffe verstehen
- Richtige Prioritäten setzen

---

## 🎯 DREAD Framework

| Faktor | Frage |
|--------|-------|
| **Damage** | Wie schlimm wäre ein Angriff? |
| **Reproducibility** | Wie leicht reproduzierbar? |
| **Exploitability** | Wie schwer ist die Ausnutzung? |
| **Affected Users** | Wie viele sind betroffen? |
| **Discoverability** | Wie leicht auffindbar? |

→ Skala: 1–10 pro Kategorie → Durchschnitt = Risikowert

---

## 🔎 STRIDE Framework

| Kategorie | Beschreibung | Verletztes Prinzip |
|-----------|--------------|---------------------|
| **Spoofing** | Identitätsfälschung | Authentication |
| **Tampering** | Datenmanipulation | Integrity |
| **Repudiation** | Abstreitbarkeit von Handlungen | Non-Repudiation |
| **Information Disclosure** | Datenlecks | Confidentiality |
| **Denial of Service** | Verfügbarkeit stören | Availability |
| **Elevation of Privilege** | Rechteausweitung | Authorization |

→ Ideal für Software- & Systemarchitekturmodellierung

---

## 🧪 PASTA Framework

**Process for Attack Simulation and Threat Analysis** – 7-Schritte-Modell:

1. **Ziele definieren**
2. **Technischer Scope**
3. **System zerlegen**
4. **Bedrohungen analysieren**
5. **Schwachstellen analysieren**
6. **Angriffsszenarien entwickeln**
7. **Risiken bewerten & Maßnahmen setzen**

💡 Besonders geeignet für Compliance & Business-getriebene Analyse

---

## ⚖️ Vergleich der Frameworks

| Framework | Fokus | Anwendungsfall |
|-----------|-------|----------------|
| **MITRE ATT&CK** | Realistische Angreifer-Techniken | Abwehrmaßnahmen bewerten |
| **DREAD** | Bewertung nach Skala | Risiko-Priorisierung |
| **STRIDE** | Kategorien von Bedrohungen | Software Threats identifizieren |
| **PASTA** | Business-zentrierter Ansatz | Ganzheitliches Risikomanagement |

---

## 📚 Fazit

- Threat Modelling = gezielter Schutz durch systematische Analyse
- Unterschiedliche Frameworks für unterschiedliche Anforderungen
- Starke Integration von **Technik**, **Risiko** & **Business-Zielen**
- Unverzichtbar für moderne Cyber-Resilienz

🔗 Weiterführend: [Atomic Red Team](https://tryhackme.com/room/atomicredteam), [CALDERA](https://tryhackme.com/room/caldera)
