# Parallele Risikomanagement-Strategie zum DASC-PM

## Ziel
Diese Strategie beschreibt, wie Risikomanagement als parallel laufende Steuerungsschicht zum DASC-PM umgesetzt wird.
DASC-PM bleibt das zentrale Delivery-Modell. Das Risikomanagement wirkt als verbindlicher Zusatzprozess, der in jeder Phase Entscheidungen absichert.

## Grundprinzip
Pro Phase des Delivery-Modells (DASC-PM) gibt es einen Risikoprozess den wir auch Steuerungsmodell nennen.
Der Risikoprozess schließt ab mit einem Risk-Gate, welches eine Entscheidung zulässt.
Die Entscheidungen sind "Freigabe", "Beobachtung" oder "Abbruch".
Der Risikoprozess beinhaltet Laufende Risikoidentifikation, Bewertung, Maßnahmensteuerung, Monitoring, Eskalation und Nachweis.

Wichtige Regel:
Ein Phasenfortschritt ohne dokumentierte Risikofreigabe ist nicht zulässig.

## Steuerungsmodell

### 1) Risk Gates an DASC-Entscheidungspunkten
Nach jeder Phase des DASC-PM gibt es ein Risk-Gate.
Standardfrage am Gate:
Ist das aktuelle Risikoprofil für den nächsten Schritt akzeptabel?

Mögliche Gate-Entscheidungen:
- Freigabe
- Freigabe mit Auflagen
- Stopp und Nachsteuerung

### 2) Einheitliches Risikoregister als Ergebnisartefakt
Alle Risiken werden in einem gemeinsamen Register geführt.
Pro Eintrag mindestens:
- Risiko-ID
- Risikotyp
- Ursache
- Auswirkung
- Eintrittswahrscheinlichkeit
- Schadenshöhe
- Risikostufe
- Owner
- Maßnahme
- KRI/Schwellenwert
- Status
- Nächster Review-Termin

### 3) Verbindliche Rollen und Verantwortungen
- Domänenexpertin oder Domänenexperte bzw. Business Owner: Business-Auswirkung, Risikoakzeptanz, Priorisierung.
- Data Scientist: Modellrisiken, Modellgüte, Drift, methodische Risiken.
- Data Engineer oder IT: Datenqualität, Pipeline-Stabilität, Betrieb und technische Kontrollen.
- Risk und Compliance: regulatorische Anforderungen, Nachweisfähigkeit, formale Eskalation.

### 4) Eskalationslogik über KRI-Schwellen
Für kritische Risiken werden messbare Key Risk Indicators definiert.
Empfohlenes 3-Stufen-Modell:
- Beobachten: Frühsignal, noch innerhalb Toleranz.
- Reagieren: Schwellenwert überschritten, Maßnahmen mit Frist.
- Eskalieren: Kritischer Wert, Entscheidung durch Governance-Ebene.

## Standardprozess pro DASC-Phase
In jeder DASC-Phase selber werden folgende Schritte durchgeführt:

1. Risiken aktualisieren / identifizieren
2. Risiken neu bewerten

Über das Risk-Gate werden folgende Schritte durchgeführt:
2. KRI auf Schwellwert anwenden
   1. Wenn Schwellwert überschritten
      1. Maßnahmen planen oder nachschärfen
      2. Maßnahmen implementieren
3. Gate-Entscheidung dokumentieren

Damit entsteht ein stabiler, wiederholbarer und auditierbarer Prozess.

## Standard-Playbooks für häufige Risikotypen

### Data Drift
- Trigger: KRI überschreitet definierten Schwellwert.
- Sofortmaßnahmen: Segmentanalyse, Ursachenprüfung, Monitoring-Intervall erhöhen.
- Folgemaßnahmen: Re-Training, Champion-Challenger-Vergleich, ggf. Rollback.
- Governance-Entscheidung: Weiterbetrieb mit Auflagen oder temporäre Einschränkung.

### Datenqualitätsrisiko
- Trigger: Fehlende Werte, Schemaänderung, Pipeline-Fehler.
- Sofortmaßnahmen: Datenstopp für betroffene Strecke, Incident-Ticket, Datenquellenprüfung.
- Folgemaßnahmen: Fix der Pipeline, Revalidierung, erneute Freigabe.

### Compliance-Risiko
- Trigger: unvollständige Dokumentation oder fehlender Nachweis.
- Sofortmaßnahmen: Freigabestopp für betroffenen Scope.
- Folgemaßnahmen: Nachweisdokumente schließen, Compliance-Review wiederholen.

## Nachweis- und Dokumentationspflicht
Jede kritische Entscheidung muss nachvollziehbar dokumentiert werden:
- Entscheidung
- Begründung
- verantwortliche Rolle
- betroffene Datenversion
- betroffene Modellversion
- wirksame Maßnahme
- Termin für Nachkontrolle

## Beispiel für die spätere Case Study (SafeLend)
Risikotyp: Feature Drift im Kredit-Scoring.

Mögliche KRI:
- Population Stability Index
- Segmentbezogene Modellgüte
- Ausfallquote im Neugeschäft

Beispielhafte Triggerlogik:
- Beobachten: PSI 0.1 bis 0.2
- Reagieren: PSI > 0.2
- Eskalieren: PSI > 0.3 oder gleichzeitiger deutlicher Performanceabfall in kritischen Segmenten

## Einordnung für die Thesis
Diese Strategie erweitert DASC-PM nicht durch ein konkurrierendes Modell.
Sie ergänzt DASC-PM um eine belastbare, phasenübergreifende Risikosteuerung mit klaren Artefakten, Rollen und Entscheidungspfaden.
Damit wird Risikomanagement von einer punktuellen Aktivität zu einem kontinuierlichen Steuerungsmechanismus.
