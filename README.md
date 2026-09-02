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
[FormSubmit](https://formsubmit.co/) (`hilfe@unfallhilfenord24.de`). Danach:

1. FormSubmit mailt die Anfrage an uns — das ist der Lead.
2. Der Besucher wird direkt auf die PDF weitergeleitet, der Download startet
   sofort. Keine Zwischenseite, kein Warten auf eine E-Mail.
3. Zusätzlich geht per Autoresponder eine Mail mit dem Link an den Besucher,
   damit er ihn später wiederfindet.

**Einmalig nötig, sonst passiert gar nichts:** Beim ersten Absenden schickt
FormSubmit eine Aktivierungsmail an `hilfe@unfallhilfenord24.de`. Bis der Link
darin geklickt ist, verschickt FormSubmit **keine einzige Mail** — auch die
Lead-Benachrichtigungen nicht. Absender ist `noreply@formsubmit.co`, landet
gern im Spam.

Grenzen, die man kennen sollte:

- Der Schutz ist **weich**, und seit der Direktweiterleitung noch weicher: die
  PDF-Adresse steht nach dem Absenden in der Adresszeile des Browsers und lässt
  sich weitergeben. Da dieses Repo öffentlich ist, ist die Datei ohnehin über
  GitHub auffindbar. Das Formular ist eine Hürde, kein Schloss.
- Die E-Mail-Adresse wird **nicht geprüft**. Wer eine erfundene Adresse
  einträgt, bekommt die PDF trotzdem. Wer verifizierte Adressen braucht, muss
  den Download an die Mail koppeln — dann aber mit dem Warten leben.
- FormSubmit sitzt in den USA. Die Datenschutzerklärung der Seite hat dafür
  einen eigenen Abschnitt bekommen — **den bitte prüfen lassen**, bevor das
  unter eigener Domain läuft. Für Dauerbetrieb ist ein EU-Dienst mit
  AV-Vertrag (z. B. Brevo) die sauberere Wahl.
- Die Einwilligung deckt **nur** den Versand der Checkliste. Für Werbung an
  diese Adressen braucht es eine gesonderte Einwilligung, in der Praxis mit
  Double-Opt-In.

## Nach der Schulung

`ideen/backlog.md` durchgehen und entscheiden: Was probieren wir zuerst aus?
Dann eine Sache auswählen, nicht fünf.
