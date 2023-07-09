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
*Dieses 00_literatur.ipynb umfasst:*
* einlesen der eingeschlossenen Literatur gemäß der Liste auf Zenodo (https://zenodo.org/record/4635599) aus dem Scoping Review von Reinecke et. al (doi: 10.3233/SHTI210546)
* Barplot mit den Jahren, Anzahl der Publikation und die fachliche Kategorie (Medizin, Medizininformatik, Informatik, Sonstiges)
* Weltkarte mit Anzahl Publikationen pro Land
* Barplot, Publikationen der Dimension Nutzung - Kategorien, pro Jahr
* Barplot, Publikationen der Dimension Nutzung, sortiert nach Kategorien und Anzeig der Multi-country bzw. single-country Datennutzung
* Sankey Diagramm - Dimensionen und Kategorien aller Publikation

Das Script 01_ohdsi_studies_analysis.ipynb enthält die Analyse und Visualisieruung der OHDSI Netzwerkstudien (Methoden Kapitel 3.3.2, Resultate Kapitel 4.2.2).  
Dieses Script enthält die Visualisierung der in OHDSI Studien verwendeten Datengruppen als Scatterplot in Kombination mit einem Histogramm zur Anzeige der Summe der Datengruppen über alle OHDSI Studien hinweg. 
Dieses Script ist in Anlehnung an die Idee zur Visualisierung von Najia Ahmadi implementiert wurden.
Vorbild dieser Visualisierung ist das GitHub Projekt von Najia Ahmadi, Release V 1.0, hier: https://github.com/NajiaAhmadi/VisualisationWithPython/releases/tag/v1.0
