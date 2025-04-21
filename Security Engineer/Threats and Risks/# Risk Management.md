# 🛡️ Risk Management (TryHackMe)

## 📘 Einführung

Risiken sind überall – auch beim Trinken von Kaffee am Schreibtisch. Dieses Modul zeigt anhand alltäglicher und technischer Beispiele, wie **Risiken erkannt, bewertet, behandelt und überwacht** werden.

### 🎯 Lernziele

| Thema | Beschreibung |
|-------|--------------|
| Begriffe | Threat, Vulnerability, Asset, Risk |
| Prozesse | Risk Framing, Risk Assessment, Response, Monitoring |
| Methoden | Qualitative & Quantitative Analyse |
| Entscheidung | Wann Risiko akzeptieren, vermeiden, übertragen, reduzieren |

---

## 🔍 Grundbegriffe

| Begriff | Beschreibung |
|--------|--------------|
| **Threat** | Bedrohung – absichtlich oder zufällig |
| **Vulnerability** | Schwachstelle – z. B. Softwarefehler, Fehlkonfiguration |
| **Asset** | Wert – Daten, Hardware, Wissen |
| **Risk** | Gefahr, dass eine Bedrohung eine Schwachstelle ausnutzt |
| **Risk Management** | Prozess zur Erkennung, Bewertung & Reaktion auf Risiken |

---

## 🧠 Arten von Bedrohungen

| Kategorie | Beispiele |
|----------|-----------|
| Menschlich | Terror, Krieg, Unruhen, Cyberangriffe, Unfälle |
| Technisch | Stromausfall, Hardwarefehler, Datenverlust |
| Natürlich | Erdbeben, Flut, Feuer |

---

## 💡 Vulnerabilities & Assets

- **Vulnerability**: z. B. offene Ports, veraltete Software, ungeschützte Logins  
- **Assets**: Server, Software, Daten, geistiges Eigentum, Dokumente

---

## 📈 Risk = Threat × Vulnerability

Risiko ergibt sich aus der Wahrscheinlichkeit, dass eine Bedrohung eine Schwachstelle ausnutzt → mit Auswirkungen auf Vertraulichkeit, Integrität oder Verfügbarkeit.

---

## 📋 Risk Management Prozess (NIST SP 800-30)

1. **Frame Risk**: Kontext und Annahmen definieren  
2. **Assess Risk**: Risiko analysieren (Impact, Wahrscheinlichkeit)  
3. **Respond to Risk**: Maßnahmen wählen  
4. **Monitor Risk**: Wirksamkeit und Änderungen verfolgen

---

## 🧱 Frame Risk

| Komponente | Beschreibung |
|------------|--------------|
| Risk Assumptions | Erwartete Bedrohungen & Folgen |
| Constraints | Budget, rechtliche Rahmen |
| Tolerance | Was ist akzeptabel? |
| Prioritäten | Was ist geschäftskritisch? |

📌 Beispiel: Buchhaltungsfirma mit hohem Risiko bei Datendiebstahl → keine Toleranz möglich.

---

## 🧪 Assess Risk

- Was sind die Bedrohungen?
- Welche Schwachstellen existieren?
- Was ist die Auswirkung?
- Wie wahrscheinlich ist es?

### 📌 Beispiele

| Szenario | Bewertung |
|---------|-----------|
| Tsunami an Küstenbüro | Bedrohung: Tsunami, Wirkung: hoch, Wahrscheinlichkeit: sehr gering |
| Ransomware an Universität | Bedrohung: Ransomware, Wirkung: Unterbrechung, Wahrscheinlichkeit: hoch |

---

## ⚖️ Risk Analysis

### Qualitativ

| Wahrscheinlichkeit | Auswirkung | Ergebnis |
|--------------------|------------|----------|
| Hoch + Hoch | Ernsthaft | 🔴 Hoch |
| Niedrig + Gering | Trivial | 🟢 Gering |

### Quantitativ

- **SLE** = AssetValue × ExposureFactor  
- **ALE** = SLE × AnnualRateOfOccurrence

📌 Beispiel:
- Laptop-Wert inkl. Daten = $10,000  
- EF = 90% → **SLE = $9,000**  
- ARO = 0.5 → **ALE = $4,500**

---

## 🛡️ Respond to Risk

| Methode | Beschreibung |
|--------|--------------|
| **Avoid** | Risiko durch Nichtstun vermeiden |
| **Transfer** | Risiko durch Versicherung teilen |
| **Mitigate** | Risiko reduzieren durch Maßnahmen |
| **Accept** | Risiko bewusst tragen |

### 🧮 Business Case: Antivirus installieren?

| Parameter | Wert |
|----------|------|
| ALE vorher | $4,500 |
| ALE nachher | $180 |
| Kosten Antivirus | $120 |
| → Value | $4,200 (positiv = sinnvoll) |

---

## 🔁 Monitor Risk

| Bereich | Ziel |
|--------|------|
| **Effectiveness** | Ist die Maßnahme noch wirksam? |
| **Change** | Neue Systeme oder Geschäftsprozesse? |
| **Compliance** | Neue Gesetze oder Audits? |

📌 Beispiel: Komplexe Passwörter → Mitarbeiter schreiben sie auf → Lösung ist ineffektiv.

---

## 🔗 Supply Chain Risk

| Typ | Beispiel |
|-----|----------|
| Hardware | Manipulierte Geräte (Hardware-Trojaner) |
| Software | Backdoors durch Entwickler |
| Dienste | Verfügbarkeit, Datenschutz beim Provider |

📌 Beispiel: Buchhaltungsfirma bezieht Computer, Software, Maildienst von Drittanbietern → Risiko entsteht auch dort.

---

## ✅ Fazit

- **Risiken sind unausweichlich**, aber **steuerbar**
- Risk Management umfasst Erkennung, Bewertung, Reaktion & Überwachung
- Nutzen aus qualitativer & quantitativer Analyse kombinieren
- Auch Dritte (Supply Chain) bergen Risiken