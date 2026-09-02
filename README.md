# anna — KI-Schulung

Ablage für die zweitägige KI-Schulung (01.–02.09.2026) und alles, was danach
daraus wird: Notizen, Prompts, Ideen, offene Fragen.

## Schnellstart während der Schulung

Alles, was dir während der Schulung begegnet, kommt in **eine** Datei:

| Was | Wohin |
|---|---|
| Mitschrift, Aha-Momente, Fragen | `notizen/tag-1.md` bzw. `notizen/tag-2.md` |
| Ein Prompt, der gut funktioniert hat | `prompts/README.md` |
| Idee für den eigenen Betrieb | `ideen/backlog.md` |
| Begriff, den du nachschlagen willst | `glossar.md` |

Nicht lange sortieren — reinschreiben, aufräumen geht später. Lieber eine
unfertige Zeile als eine verlorene Idee.

## Struktur

```
notizen/     Mitschriften pro Tag (VORLAGE.md zum Kopieren)
prompts/     Prompts, die sich bewährt haben — mit Kontext, wofür
ideen/       Was wir im Betrieb damit machen könnten (Backlog)
glossar.md   Begriffe aus der Schulung, in eigenen Worten
website/     In der Schulung gebaute Seiten (siehe unten)
CLAUDE.md    Kontext für Claude-Sessions in diesem Repo
```

## website/ — was während der Schulung entstanden ist

Hier liegen fertige Arbeitsergebnisse, keine Notizen. Sie bleiben bewusst in
diesem Repo: Sie sind Teil der Schulung, nicht Teil des laufenden Betriebs.

| Datei | Was es ist |
|---|---|
| `unfallhilfe-nord-24.html` | Konversionsorientierte Landingpage für Unfallhilfe Nord 24, gebaut aus einem Kunden-Briefing. Eine einzige Datei, läuft per Doppelklick, keine externen Abhängigkeiten. |
| `freebie/danke.html` | Seite nach dem Absenden des Formulars. |
| `freebie/ce5c8f7cde3d/…pdf` | Die Checkliste. Liegt bewusst unter einem nicht erratbaren Pfad und ist **nirgends verlinkt** — den Link bekommt nur, wer das Formular ausfüllt. |

Die Quelldatei der Checkliste liegt **außerhalb** von `website/`, unter
`freebie-quelle/unfallcheckliste.html`. Das ist Absicht: alles in `website/`
wird veröffentlicht, und die Quelle würde den Inhalt am Formular vorbei
verfügbar machen. Dort ändern, nie die PDF direkt, dann neu erzeugen:

```bash
chromium --headless --no-pdf-header-footer \
  --print-to-pdf=website/freebie/ce5c8f7cde3d/unfallcheckliste-unfallhilfe-nord-24.pdf \
  freebie-quelle/unfallcheckliste.html
```

### Leads: wie der Download abläuft

Das Formular im Abschnitt „Zum Mitnehmen" schickt an
[FormSubmit](https://formsubmit.co/) (`hilfe@unfallhilfenord24.de`). FormSubmit
mailt die Anfrage an uns und schickt dem Interessenten automatisch den
Download-Link.

**Einmalig nötig:** Beim ersten Absenden schickt FormSubmit eine
Aktivierungsmail an `hilfe@unfallhilfenord24.de`. Erst nach dem Klick darauf
funktioniert das Formular. Also einmal selbst ausfüllen und bestätigen.

Grenzen, die man kennen sollte:

- Der Schutz ist **weich**. Die PDF liegt unter einer öffentlichen Adresse, nur
  unter einem schwer zu erratenden Pfad. Wer den Link weitergibt, gibt die
  Datei weiter. Und da dieses Repo öffentlich ist, ist die Datei ohnehin über
  GitHub auffindbar. Gegen Google und beiläufiges Teilen hilft es, gegen
  jemanden der sucht nicht.
- FormSubmit sitzt in den USA. Die Datenschutzerklärung der Seite hat dafür
  einen eigenen Abschnitt bekommen — **den bitte prüfen lassen**, bevor das
  unter eigener Domain läuft. Für Dauerbetrieb ist ein EU-Dienst mit
  AV-Vertrag (z. B. Brevo) die sauberere Wahl.
- Die Einwilligung deckt **nur** den Versand der Checkliste. Für Werbung an
  diese Adressen braucht es eine gesonderte Einwilligung, in der Praxis mit
  Double-Opt-In.

### Wo die Seite online steht

**https://thomaskraft-ki.github.io/anna/**

Ausgeliefert wird der Branch `gh-pages`. Der Workflow
`.github/workflows/pages.yml` schreibt den Inhalt von `website/` bei jeder
Änderung auf `main` dorthin — also nichts von Hand nach `gh-pages` kopieren,
immer `website/` ändern.

Die Landingpage steht bewusst auf `noindex` (Zeile 14 im HTML), damit sie
`unfallhilfenord24.de` keine Rankings wegnimmt. Sie ist erreichbar und
teilbar, taucht aber nicht bei Google auf.

Die Adresse oben ist eine Übungs- und Vorschauadresse. Wenn die Seite unter
der eigenen Domain laufen soll, gehört sie in das Repo der jeweiligen Marke
(`www-unfallhilfenord24-de`) — dort mit Domain, Canonical und ohne `noindex`.

## Nach der Schulung

`ideen/backlog.md` durchgehen und entscheiden: Was probieren wir zuerst aus?
Dann eine Sache auswählen, nicht fünf.
