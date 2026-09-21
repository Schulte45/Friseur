# Übernahmeprotokoll: Schreiben bei Fehlzeiten (Stufe 1 und Stufe 2)

Stand: 21.09.2026. Dieses Protokoll fasst einen Chat zusammen, der im falschen Gespräch geführt wurde. Es soll im richtigen Chat (dem, in dem die Teilnehmerinnen-App entwickelt wurde) eingelesen werden, damit dort nahtlos weitergearbeitet werden kann. Bitte alles als gegeben übernehmen und nur die unter „Offene Punkte“ genannten Dinge nachfragen.

## 1. Auftrag in einem Satz

Zwei Schreiben an Teilnehmerinnen (Stufe 1: Hinweis, Ausbildungsziel gefährdet; Stufe 2: Abmahnung), die ihre Daten (Namen, Kontaktdaten, Fehlzeiten) automatisch aus dem System bzw. der App bekommen und automatisch per E-Mail versendet werden können, ohne dass jemand Excel-Tabellen pflegen oder Serienbriefe von Hand zusammenbauen muss.

## 2. Kontext

- Träger: BWK BildungsWerk in Kreuzberg GmbH, Cuvrystraße 34, 10997 Berlin.
- Koordination und Unterzeichnerin: Kerstin Pfrötzschner.
- Umschulungsprogramm mit Teilnehmerinnen (die TN-Import-Vorlage heißt „Teilnehmerinnen“, daher wurden die Briefe weiblich formuliert, siehe Offene Punkte).
- Kostenträger ist zum Beispiel die Agentur für Arbeit oder das Jobcenter.
- Nutzer: Uwe Schulte. Er möchte kurze, einfache Antworten auf Deutsch, wenig Rückfragen und möglichst wenig Handarbeit. Die bisherigen Lösungen (Excel plus Word-Serienbrief) empfand er als zu kompliziert.

## 3. Regeln der beiden Stufen

| | Stufe 1: Hinweisschreiben | Stufe 2: Abmahnung |
|---|---|---|
| Auslöser | Gesamtzahl aller Fehltage überschreitet Grenzwert | Zahl der unentschuldigten Fehltage überschreitet Grenzwert |
| Was zählt | krank + entschuldigt + unentschuldigt | nur unentschuldigt |
| Ton | höflich, aber bestimmt: Ausbildungsziel ist gefährdet | formal, sachlich, Abmahnung mit Androhung des Ausschlusses |
| Kostenträger | nicht erwähnt | wird informiert, Ausschluss beendet in der Regel die Förderung |

Weitere Regeln:

- „Verspätet“ gilt nur zusammen mit „Anwesend“ und ist kein Fehltag. „Anwesend“ und „Verspätet“ werden nie mitgezählt.
- Die Grenzwerte hat der Nutzer noch nicht genannt. Die Beispielwerte 10 (Stufe 1) und 3 (Stufe 2) sind von mir erfunden. Sie müssen konfigurierbar sein. „Überschritten“ wurde als „größer als“ umgesetzt.
- Wer beide Grenzen überschreitet, steht in beiden Läufen. Der Mensch entscheidet, welches Schreiben rausgeht.
- Teilnehmerinnen mit Status Bestanden, Abgebrochen oder Unterbrochen bekommen keinen Brief.

## 4. Datenmodell der App (aus der hochgeladenen Datei TN-Import-Vorlage.xlsx)

Spalten des Blatts „Teilnehmerinnen“: Vorname *, Nachname *, Geburtsdatum, Telefon, E-Mail, Straße Hausnr., PLZ / Ort, Eintrittsart (Regulärer Start, Quereinstieg), Eintrittsdatum, Status (Aktiv, Verlängerung, Unterbrochen, Bestanden, Abgebrochen), Kostenträger / Fördermittelgeber, Aktenzeichen / Kundennummer. Datumsformat TT.MM.JJJJ. Es gibt keine Spalte für Anrede und keine für die Berufsbezeichnung.

Die Fehlzeiten selbst werden laut Nutzer in der App vermerkt. Bekannt sind nur die Anwesenheitskategorien „Anwesend“ und „Verspätet“ (Aussage des Nutzers). Die Kategorien Krank, Entschuldigt und Unentschuldigt wurden von mir angenommen, weil beide Stufen sie brauchen. Das Datenmodell der Anwesenheit in der App habe ich nicht gesehen.

## 5. Datenfelder, die die Schreiben brauchen

| Feld | Bedeutung |
|---|---|
| Vorname, Nachname | aus dem Teilnehmerinnen-Datensatz |
| Strasse, PLZ_Ort | Adresse |
| E_Mail | Empfängeradresse für die Mail |
| Kostentraeger | zum Beispiel Agentur für Arbeit oder Jobcenter |
| Aktenzeichen_Zeile | „Aktenzeichen / Kundennummer: …“, leer wenn keines vorhanden |
| Zeitraum_von, Zeitraum_bis | Betrachtungszeitraum der Fehltage |
| Fehltage_krank, Fehltage_entschuldigt, Fehltage_unentschuldigt, Fehltage_gesamt | Anzahl im Zeitraum, gesamt = Summe der drei |
| Grenzwert_gesamt, Grenzwert_unentschuldigt | Konfiguration Stufe 1 und Stufe 2 |
| Stufe1_faellig, Stufe2_faellig | „Ja“ oder „Nein“ |
| Tage_Liste | die unentschuldigten Tage als Text, zum Beispiel „12.08.2026, 13.08.2026, 02.09.2026“ |
| Frist_Rueckmeldung | Frist für den Gesprächstermin in Stufe 1 |
| Frist_Stellungnahme, Frist_Gespraech | Fristen in Stufe 2 |
| Hinweis_Vorschreiben_Satz | optionaler Satz „Wir hatten Sie bereits mit Schreiben vom [Datum] auf Ihre Fehlzeiten und die Gefährdung Ihres Ausbildungsziels hingewiesen.“, nur wenn ein früheres Hinweisschreiben (Stufe 1) protokolliert ist |

## 6. Freigegebene Texte

Der Nutzer hat Schreiben 2 (Abmahnung) als „perfekt“ freigegeben und Schreiben 1 nach mehreren Korrekturen als „sehr gut“. Die folgenden Texte sind die aktuelle Fassung. Platzhalter stehen als {{Feld}}.

### Schreiben 1: Hinweis (Stufe 1)

Betreff: **Ihre Fehlzeiten in der Umschulung – Gefährdung des Ausbildungsziels**

Sehr geehrte Frau {{Nachname}},

mit diesem Schreiben weisen wir Sie auf Ihre Fehlzeiten in der Umschulung hin. Sie sind inzwischen so hoch, dass Ihr Ausbildungsziel gefährdet ist.

Nach unseren Aufzeichnungen haben Sie im Zeitraum vom {{Zeitraum_von}} bis {{Zeitraum_bis}} insgesamt **{{Fehltage_gesamt}} Fehltage** angesammelt, darunter {{Fehltage_krank}} krankheitsbedingte, {{Fehltage_entschuldigt}} entschuldigte und {{Fehltage_unentschuldigt}} unentschuldigte Tage. Damit haben Sie die zulässige Grenze von **{{Grenzwert_gesamt}} Fehltagen** überschritten.

Bitte bedenken Sie: Die Umschulung ist eng getaktet, und die Lerninhalte bauen aufeinander auf. Bei diesem Umfang an Fehlzeiten lässt sich der versäumte Stoff kaum noch nachholen. Es besteht die konkrete Gefahr, dass Sie die Anforderungen der Abschlussprüfung nicht erfüllen und Ihr Ausbildungsziel, den erfolgreichen Abschluss der Umschulung, nicht erreichen.

Bitte melden Sie sich bis zum **{{Frist_Rueckmeldung}}** unter 030 617929-0 oder kontakt@bwk-berlin.de bei uns und vereinbaren Sie einen Gesprächstermin. Bei gesundheitlichen, familiären oder organisatorischen Schwierigkeiten sprechen Sie uns bitte offen an, dann suchen wir gemeinsam nach Lösungen.

Bitte beachten Sie: Fehlzeiten sind gemäß Teilnahmevertrag am ersten Fehltag zu melden, Krankheitstage sind spätestens ab dem dritten Tag ärztlich nachzuweisen. Bei weiteren Fehlzeiten prüfen wir Ihre weitere Teilnahme und leiten weitere Schritte ein.

Mit freundlichen Grüßen
Kerstin Pfrötzschner, Koordination

Feedback des Nutzers zur Tonalität, bitte beibehalten: Der Satz „Das ist kein Vorwurf“ ist gestrichen worden. Formulierungen wie „möchten wir Sie aufmerksam machen“ waren zu weich, „Wir müssen Ihnen deutlich sagen“ und „Wir erwarten“ zu hart. Die jetzt verwendeten Formulierungen „weisen wir Sie hin“, „Bitte bedenken Sie“ und „Bitte melden Sie sich bis zum …“ hat er als „sehr gut“ bestätigt.

### Schreiben 2: Abmahnung (Stufe 2)

Betreff: **Abmahnung wegen unentschuldigter Fehlzeiten**
Darunter: {{Aktenzeichen_Zeile}}

Sehr geehrte Frau {{Nachname}},

wir mahnen Sie hiermit wegen unentschuldigter Fehlzeiten in der Umschulung ab.

**Sachverhalt:** Sie haben im Zeitraum vom {{Zeitraum_von}} bis {{Zeitraum_bis}} an insgesamt **{{Fehltage_unentschuldigt}} Tagen** unentschuldigt gefehlt. Damit haben Sie die Grenze von **{{Grenzwert_unentschuldigt}} unentschuldigten Fehltagen** überschritten. Im Einzelnen handelt es sich um folgende Tage, für die weder eine Meldung noch ein Nachweis vorliegt: {{Tage_Liste}}.

**Pflichtverletzung:** Als Teilnehmerin sind Sie nach Ihrem Teilnahmevertrag zur regelmäßigen und pünktlichen Teilnahme am Unterricht verpflichtet. Fehlzeiten sind am ersten Fehltag zu melden, Krankheitstage sind spätestens ab dem dritten Tag durch eine ärztliche Bescheinigung nachzuweisen. Dieser Pflicht sind Sie für die oben genannten Tage nicht nachgekommen. {{Hinweis_Vorschreiben_Satz}}

**Aufforderung:** Wir fordern Sie auf, künftig regelmäßig und pünktlich am Unterricht teilzunehmen, jede Verhinderung am ersten Fehltag zu melden und Krankheitstage fristgerecht nachzuweisen. Diese Abmahnung wird zu Ihrer Teilnehmerakte genommen.

**Konsequenzen:** Wir weisen Sie ausdrücklich darauf hin, dass weitere unentschuldigte Fehlzeiten zu Ihrem Ausschluss aus der Maßnahme führen können, etwa durch außerordentliche Kündigung des Teilnahmevertrags. Ihr Kostenträger ({{Kostentraeger}}) wird von uns über diese Abmahnung informiert. Ein Ausschluss beendet in der Regel auch die Förderung Ihrer Umschulung und kann Folgen für Ihren Leistungsanspruch haben. Ihr Ausbildungsziel, den erfolgreichen Abschluss der Umschulung, würden Sie dann nicht erreichen.

**Stellungnahme:** Sind Sie der Auffassung, dass die genannten Fehltage zu Unrecht als unentschuldigt erfasst wurden, oder können Sie Gründe nachweisen (zum Beispiel durch eine ärztliche Bescheinigung), legen Sie uns dies bitte bis zum **{{Frist_Stellungnahme}}** schriftlich vor. Wir prüfen Ihre Angaben und berücksichtigen sie. Unabhängig davon bieten wir Ihnen ein Gespräch an. Bitte vereinbaren Sie dazu bis zum **{{Frist_Gespraech}}** einen Termin unter 030 617929-0 oder kontakt@bwk-berlin.de. Wenn Sie in einer schwierigen Situation sind, sprechen Sie uns an, denn wir möchten, dass Sie Ihre Umschulung erfolgreich abschließen.

Mit freundlichen Grüßen
Kerstin Pfrötzschner, Koordination

Am Ende der Fassung mit Briefpapier steht eine Empfangsbestätigung (Ort, Datum, Unterschrift der Teilnehmerin, mit dem Hinweis, dass die Bestätigung keine Zustimmung zum Inhalt bedeutet). In der Mailfassung steht stattdessen: „Bitte bestätigen Sie uns den Erhalt dieser Abmahnung durch eine kurze Antwort auf diese E-Mail. Die Bestätigung bedeutet nicht, dass Sie dem Inhalt zustimmen.“

Hinweis: Die zuerst freigegebene Fassung von Schreiben 2 war dieselbe, hatte aber „Teilnehmerin bzw. Teilnehmer“, eine Berufsbezeichnung im Betreff und im Text, eine Tabelle der Fehltage statt der Tage-Liste, den Vermerk „Einschreiben mit Rückschein“ und eine Empfangsbestätigung mit Unterschrift. Für die Automatisierung wurden Tabelle, Berufsbezeichnung und Einschreiben-Vermerk entfernt, weil die Daten dafür in der Teilnehmerinnen-Vorlage fehlen.

## 7. Versand und Layout

- **Versand:** Der Nutzer will, dass das Anschreiben automatisch in der Mail landet: entweder als Anhang oder, wenn nicht als Anhang, dann als Mailinhalt selbst. Entschieden wurde: Der vollständige Brieftext steht als Mailinhalt (ohne Briefpapier) und das Schreiben zusätzlich als PDF auf Briefpapier im Anhang. Der Mailtext endet mit dem Hinweis, dass das Schreiben zusätzlich als PDF im Anhang liegt.
- **Betreffzeilen der Mail:** Stufe 1: „Ihre Fehlzeiten in der Umschulung – Gefährdung des Ausbildungsziels“. Stufe 2: „Abmahnung wegen unentschuldigter Fehlzeiten“.
- **Mailsignatur:** Kerstin Pfrötzschner, Koordination, BWK BildungsWerk in Kreuzberg GmbH, Cuvrystraße 34 · 10997 Berlin, Tel. 030 617929-0 · kontakt@bwk-berlin.de · www.bwk-berlin.de. Telefon und E-Mail stammen aus dem Briefpapier und sind die allgemeinen Kontaktdaten, nicht die Durchwahl der Koordinatorin.
- **Briefpapier:** Der Nutzer hat zwei Vorlagen hochgeladen: „20210504_Briefvorlage.doc“ (erste Seite, Logo, Absenderzeile „BWK BildungsWerk in Kreuzberg GmbH · Cuvrystraße 34 · 10997 Berlin“ und Seitenleiste mit Adressen, Bankverbindungen und Zertifizierungen, Falzmarken) und „Briefvorlage digital - BWK Seite 2 002.doc“ (Folgeseite nur mit Logo). Seite 1: Ränder links 1418, rechts 3119, oben 3055, unten 1701 (Twips), Schrift Arial 10 pt. Die Empfängeradresse beginnt direkt unter der Absenderzeile im Hintergrundbild. Das Hintergrundbild ist ein großes PNG in der Kopfzeile der ersten Seite. Folgeseiten: Logo aus der zweiten Vorlage, Seitenzahl unten links („Seite X“).

## 8. Was in diesem Chat gebaut wurde

Alle Dateien liegen der Übergabe bei.

- `Serienbrief_1_Hinweis_Fehltage_BWK.docx` und `Serienbrief_2_Abmahnung_BWK.docx`: Briefe auf dem BWK-Briefpapier, mit Word-Serienbrieffeldern (MERGEFIELD) für alle Felder aus Abschnitt 5. Ein SKIPIF-Feld am Anfang überspringt alle, deren Stufe1_faellig bzw. Stufe2_faellig nicht „Ja“ ist.
- `Serienmail_1_Hinweis_Fehltage.docx` und `Serienmail_2_Abmahnung.docx`: dieselben Briefe ohne Briefpapier, gedacht als Mailinhalt für den Word-Serienversand.
- `Fehlzeiten_Auswertung.xlsx`: Blatt „Teilnehmerinnen“ mit den Spalten der TN-Import-Vorlage plus einer optionalen Spalte „Datum_Hinweisschreiben“, Blatt „Rohdaten“ (Fehlzeiten-Export: Nachname, Vorname, Datum, Status), Blatt „Einstellungen“ (Zeitraum, Grenzwerte, Fristen, Statusbezeichnungen), Blatt „Serienbrief“ (rechnet alles selbst) und Blatt „Anleitung“. Die Beispieldaten (Maria Musterfrau, Anna Beispiel) sind erfunden.
- Ältere Fassungen: Schreiben_1/2 als .docx, PDF, .eml-Mailentwurf und .txt-Mailtext mit Platzhaltern in eckigen Klammern. Die Texte in Abschnitt 6 sind neuer als diese Dateien.
- Zwei Claude-Docs mit den ersten Textfassungen: Schreiben 1 (`https://claude.ai/code/artifact/10db1557-7056-410f-957a-a5a1912ba729`) und Schreiben 2 (`https://claude.ai/code/artifact/50d80af1-3510-4544-86dd-a8094fdad2dc`). Sie enthalten noch die eckigen Klammern und die ältere Berufsbezeichnung.

Was nicht geprüft ist: Die Word-Serienbriefe wurden nicht in Word getestet, nur per LibreOffice gerendert und schema-validiert. Die Excel-Formeln (COUNTIFS, TEXTJOIN als Matrixformel) wurden mit LibreOffice nachgerechnet. TEXTJOIN braucht Excel 2019 oder 365.

## 9. Offene Punkte und Annahmen

1. **Grenzwerte und Fristen** sind nicht festgelegt (nur Beispielwerte).
2. **Anwesenheitsdaten der App:** Wie sind sie gespeichert, und gibt es die Kategorien Krank, Entschuldigt und Unentschuldigt tatsächlich so? Wie heißen sie genau?
3. **Anrede:** Die Briefe sprechen alle mit „Sehr geehrte Frau …“ und „Teilnehmerin“ an, weil die Vorlage nur „Teilnehmerinnen“ kennt. Das bitte bestätigen. Falls es auch männliche oder diverse Teilnehmende gibt, braucht die App ein Anredefeld.
4. **Berufsbezeichnung:** Gibt es nicht in der Vorlage. Die Briefe sagen deshalb „Abschluss der Umschulung“.
5. **Feste Formulierungen, nicht vom Nutzer bestätigt:** „gemäß Teilnahmevertrag“, „Krankheitstage spätestens ab dem dritten Tag ärztlich nachzuweisen“ und die Kontaktdaten 030 617929-0 und kontakt@bwk-berlin.de.
6. **Rechtliches:** Die Abmahnung sollte vor dem ersten Versand rechtlich geprüft werden (Zustellung per E-Mail, Nachweis des Zugangs, Nennung des Kostenträgers, Vertragsgrundlage). Ich bin keine Rechtsberaterin.
7. **Zugang zur App:** In diesem Chat gab es keinen Zugriff auf die App. Der Ordner der App war nicht mit Cowork verbunden.

## 10. Gewünschte Lösung für den neuen Chat

Der Nutzer hat klar gesagt: Die Daten sind alle schon im System (Kontaktdaten, Namen, Fehlzeiten). Das Schreiben-Tool soll darauf zugreifen, ohne dass er Tabellen pflegt und exportiert. Mein Vorschlag, den er noch nicht bestätigt hat: Die App bekommt eine Funktion „Fehlzeiten-Schreiben“.

- Sie zählt automatisch pro Teilnehmerin (mit Status Aktiv oder Verlängerung) im gewählten Zeitraum die Fehltage nach Kategorie.
- Sie zeigt eine Liste, wer die Grenze von Stufe 1 bzw. Stufe 2 überschritten hat (Grenzwerte und Fristen einstellbar).
- Sie erzeugt pro Person das Schreiben aus Abschnitt 6 mit den Feldern aus Abschnitt 5, als Vorschau, als E-Mail-Entwurf (zum Beispiel .eml mit Betreff, Mailinhalt und PDF-Anhang) und als PDF oder Word-Datei auf dem BWK-Briefpapier.
- Sie merkt sich, wer wann welches Schreiben bekommen hat. Dadurch entfällt die optionale Spalte „Datum_Hinweisschreiben“ und der Satz zum früheren Hinweisschreiben in der Abmahnung füllt sich selbst.

Die Excel-und-Word-Lösung aus Abschnitt 8 ist der Notbehelf, falls die App nicht angepasst werden kann.
