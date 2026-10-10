# KI-Exposition und Löhne: Eine empirische Analyse

Bachelorarbeit im Studiengang Wirtschaftswissenschaften (Ondokuz Mayıs Üniversitesi)

[![In Colab öffnen](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/muhammed-emin-esmer/bachelor-thesis/blob/main/Untitled0.ipynb)

Dieses Projekt untersucht, wie die **Exposition eines Berufs gegenüber künstlicher Intelligenz** mit dem **Lohnniveau** in diesem Beruf zusammenhängt. Grundlage sind Daten zu **565 Berufen** aus dem US-Arbeitsmarkt. Die gesamte Analyse läuft in Python (Google Colab).

---

## Fragestellung

> Zeigen Berufe mit höherer KI-Exposition ein höheres oder niedrigeres Lohnniveau als Berufe mit geringer KI-Exposition?

## Kernergebnis

**Berufe mit höherer KI-Exposition verdienen im Schnitt deutlich mehr.** Teilt man die 565 Berufe nach ihrem AIOE-Wert in vier gleich große Gruppen, steigt der durchschnittliche Medianlohn von etwa **59.100 USD** im untersten Viertel auf etwa **89.100 USD** im obersten Viertel. Das entspricht einem Unterschied von rund **50 %**. Auch der mittlere Wert (Median der Berufe) liegt im obersten Viertel mit 84.150 USD um etwa 48 % über dem untersten Viertel (57.010 USD).

| KI-Expositionsgruppe | Berufe | Ø Medianlohn (USD/Jahr) | Median der Berufe (USD/Jahr) |
|---|---:|---:|---:|
| Q1 (niedrigste Exposition) | 142 | 59.142 | 57.010 |
| Q2 | 141 | 62.819 | 60.600 |
| Q3 | 141 | 78.107 | 72.490 |
| Q4 (höchste Exposition) | 141 | 89.107 | 84.150 |

![Lohn und KI-Exposition](abbildungen/ai_wage_analysis.png)

> Der Zusammenhang ist **deskriptiv**. Er bedeutet nicht, dass KI-Exposition Löhne erhöht. Hoch exponierte Berufe sind oft Tätigkeiten mit hoher Qualifikation (z. B. Management, Finanzen), was den Lohnunterschied erklären kann.

---

## Daten

| Quelle | Datei | Inhalt |
|---|---|---|
| Felten, Raj & Seamans: AIOE-Index (AI Occupational Exposure) | `AIOE_DataAppendix.xlsx` (Blatt "Appendix A") | KI-Expositionswert (AIOE) pro Beruf |
| U.S. Bureau of Labor Statistics (BLS), Lohndaten Mai 2024 | `national_owner_M2024_dl.xlsx` | Medianer Jahreslohn (`A_MEDIAN`) und Beschäftigung (`TOT_EMP`) pro Beruf |

BLS-Daten: https://www.bls.gov/oes/

> Die Rohdaten sind öffentlich verfügbar und liegen nicht in diesem Repository. Zum Ausführen müssen beide Dateien im Notebook hochgeladen werden.

---

## Methodik

1. **Filtern:** Aus den BLS-Daten werden branchenübergreifende Gesamtzeilen (`OWN_CODE` 123) auf der Ebene der Detailberufe behalten (715 Zeilen).
2. **Zusammenführen:** Verknüpfung beider Datensätze über den SOC-Berufscode (`SOC Code` bzw. `OCC_CODE`). Nach Entfernen fehlender Werte (`*` in den BLS-Daten) bleiben **565 Berufe**.
3. **Gruppenbildung:** Einteilung der Berufe in vier gleich große Gruppen nach AIOE-Wert (Quartile).
4. **Deskriptive Analyse und Visualisierung:** Boxplot und Balkendiagramm der Löhne je Quartil, Streudiagramm AIOE gegen Medianlohn mit linearer Trendlinie, Vergleich der zehn Berufe mit der höchsten und der niedrigsten Exposition.

---

## Projektstruktur

```
.
├── README.md
├── Untitled0.ipynb            # Gesamte Analyse (Google Colab)
└── abbildungen/
    └── ai_wage_analysis.png   # Ergebnisgrafik
```

---

## Ausführen

**Google Colab (empfohlen):** Über das Badge oben öffnen, alle Zellen der Reihe nach ausführen und die beiden Excel-Dateien beim Upload auswählen.

**Lokal:**

```bash
git clone https://github.com/muhammed-emin-esmer/bachelor-thesis.git
cd bachelor-thesis
pip install pandas numpy matplotlib seaborn openpyxl jupyter
jupyter notebook
```

Hinweis: Die erste Code-Zelle nutzt `google.colab.files` und funktioniert nur in Colab. Lokal müssen die Excel-Dateien direkt mit `pd.read_excel(...)` aus dem Projektordner geladen werden.

---

## Verwendete Werkzeuge

- Python
- pandas, NumPy (Datenaufbereitung, Trendlinie)
- matplotlib, seaborn (Visualisierung)
- Google Colab

---

## Einschränkungen

- Die Analyse zeigt **Zusammenhänge, keine Kausalität**; es werden keine Kontrollvariablen verwendet.
- Der AIOE-Index misst die **potenzielle** Exposition eines Berufs gegenüber KI, nicht die tatsächliche Nutzung.
- Verwendet wird der **mediane Jahreslohn pro Beruf**, kein individueller Lohn und keine Lohnprämie.
- Die Daten beziehen sich auf den **US-Arbeitsmarkt (2024)**; eine Übertragung auf andere Länder ist nur eingeschränkt möglich.

---

## Quellen

- Felten, E., Raj, M., & Seamans, R. (2021): *Occupational, industry, and geographic exposure to artificial intelligence: A novel dataset and its potential uses.* Strategic Management Journal.
- U.S. Bureau of Labor Statistics: Occupational Employment and Wage Statistics (OEWS), Mai 2024.

---

## Autor

**Muhammed Emin Esmer**
Wirtschaftswissenschaften, Ondokuz Mayıs Üniversitesi
GitHub: https://github.com/muhammed-emin-esmer · E-Mail: meesmer36@gmail.com
