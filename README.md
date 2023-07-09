# dissertation-code

Dieses Projekt ist Bestandteil der Dissertation von Ines Reinecke
vorgelegt am 11.07.2023 an der Technischen Universität Dresden, Medizinische Fakultät

## Struktur des Projektes

Der Ordner "data_in" enthält die Daten, welche von den Jupyter Notebooks gelesen werden.
Nicht enthalten in diesem Projekt sind die Dateien:
* DS-Med initiale Version
* DS-Med Version mit verbesserter Datenstruktur nach Durchführung der entsprechenden Maßnahmen (Zuordnung der ATC Codes und Validierung der Ergebnisse für die TOP1000)
* DS-Katalog

Der Ordner "data_results" enthält die Ergebnisse der Jupyter Notebooks. 

### Ordner 00_literatur

Hier sind die Analysen der Literatur des Scoping Reviews von Reinecke et al. enthalten. 
Das Script 00_literatur.ipynb enthält die komplette Analyse und Visualisierung der in das Scoping Review eingeschlossenen Literatur (Methoden Kapitel 3.2, Resultate Kapitel 4.1).  
**Dieses Script 00_literatur.ipynb umfasst:**
* einlesen der eingeschlossenen Literatur gemäß der Liste auf Zenodo (https://zenodo.org/record/4635599) aus dem Scoping Review von Reinecke et. al (doi: 10.3233/SHTI210546)
* Barplot mit den Jahren, Anzahl der Publikation und die fachliche Kategorie (Medizin, Medizininformatik, Informatik, Sonstiges)
* Weltkarte mit Anzahl Publikationen pro Land
* Barplot, Publikationen der Dimension Nutzung - Kategorien, pro Jahr
* Barplot, Publikationen der Dimension Nutzung, sortiert nach Kategorien und Anzeig der Multi-country bzw. single-country Datennutzung
* Sankey Diagramm - Dimensionen und Kategorien aller Publikation

Das **Script 01_ohdsi_studies_analysis.ipynb** enthält die Analyse und Visualisieruung der OHDSI Netzwerkstudien (Methoden Kapitel 3.3.2, Resultate Kapitel 4.2.2).  
Dieses Script enthält die Visualisierung der in OHDSI Studien verwendeten Datengruppen als Scatterplot in Kombination mit einem Histogramm zur Anzeige der Summe der Datengruppen über alle OHDSI Studien hinweg. 
Dieses Script ist in Anlehnung an die Idee zur Visualisierung von Najia Ahmadi implementiert wurden.
Vorbild dieser Visualisierung ist das GitHub Projekt von Najia Ahmadi, Release V 1.0, hier: https://github.com/NajiaAhmadi/VisualisationWithPython/releases/tag/v1.0

### Ordner 01_data_structure

Hier sind alle Jupyter Notebooks, die im Rahmen der Durchführung der Maßnahmen zur Verbesserung der Datenstruktur der Medikationsverordnungen (Methode Kapitel 3.5.2) implementiert wurden, abgelegt.  

**Script 01_Datenstruktur_Algorithmen_Implementierung.ipynb beinhaltet:**  
Zunächst werden die Rohdaten aus Datensatz DS-Med (Medikationsverordnungen) und Datensatz DS-Katalog (Arzneimittelkatalog des UKD) eingelesen.  
Anschließend wird der Datensatz DS-Med wie folgt im Detail geprüft:  
* Summe der Arzneimittelverordnungen der Jahre 2016 bis 2020
* Ermittlung der fehlenden Arzneimitteleinträge in den Arzneimittelverordnungsdaten 
* Ermittlung der Menge der unstrukturierten Arzneimittelverordnungsdaten
* Gruppierung der unstrukturierten Arzneimittelverschreibungsdaten nach Medikationstext und Berechnung der Häufigkeit
* Überprüfung der Gesamtzahl der verschiedenen unstrukturierten Einträge für den Medikationstext
* Verteilung der Freitext-Arzneimittelverordnungen nach Häufigkeit auswerten
* Prüfung, ob die ersten 1000 häufigsten unstrukturierten Arzneimittelverordnungen für die manuelle Auswertung ausreichen, um das Ziel von 80% aller Arzneimittelverordnungen mit ATC-Code zu erreichen 
* Ausführen des Algorithmus auf den unstrukturierten Daten zur Bestimmung des ATC-Codes in STEP1 (Regex-Medikamentenprodukt), STEP2 (Inhaltsstoff) und STEP 3 (NLP basierend auf Ähnlichkeit mit Levenshtein-Distanz) - STEP 3 liefert bis zu 3 verschiedene vorgeschlagene ATC-Codes
* Ergebnisse zurückgeben und die häufigsten 1000 Einträge und Ergebnisse für Algorithmus 1, 2 und 3 erstellen
* Vorbereitung der Zahlen für die Visualisierung im Venn Chart, Übereinstimmung der Ergebnisse der Algorithmen


**Script 02_Datenstruktur_Ergebnisse_Visualisierung_Übereinstimmung.ipynb beinhaltet:**  
* Visualisierung der Übereinstimmung der Ergebnisse der Algorithmen auf die Medikationsverordnungen
* Visualisierung Venn Diagramm, Abbildung 4.9, Kapitel Ergebnisse, Maßnahmen - Datenstruktur, Algorithmen (Kapitel 4.4.2.1)

**Script 03_t-test-Algorithmus3-LevenshteinÄhnlichkeit.ipynb beinhaltet:**  
* Eingelesene Daten - Datensatz DS-Top1000
* Generieren von zwei Dataframes für die korrekten und nicht korrekten Ergebnisse von Algorithmus 3
* statistische Informationen generieren für die beiden neuen Dataframes in Bezug auf Algorithmus 3 und den Ähnlichkeitswert von Levenshtein
* Durchführung eines beidseitigen t-tests um zu prüfen, ob sich die Ähnlichkeitswerte des Algorithmus 3 für die beiden Ergebnismengen signifikant unterscheiden

**Script 04_ATC_Codes_Anwenden_DatenVisualisierung.ipynb beinhaltet:**  
* Einlesen des Datensatzes DS-Med und DS-Top1000
* Generierung einer neuen Spalte "ATC-Correct" in DS-Top1000
* Zusammenführen (Merge) der beiden Datensätze DS-Med und DS-Top1000 basierend auf der Spalte "MEDICATION" - nur für die unstrukturierten Medikationsverordnungen
* Generierung eines finalen Datensatzes von DS-Med, bei dem alle ATC Codes, die durch Algorithmus 3 zugeordnet werden in einer Spalte enthalten sind - nur für die Freitexte, die Teil von DS-Top1000 sind und manuell validiert wurden
* Generierung eines Datensatzes als Eingangsgröße für das Streudiagramm der Visualisierung - Strukturiertheit auf Basis von ATC Code



