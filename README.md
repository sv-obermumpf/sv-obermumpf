# Schiessverein Obermumpf

Mehrseitige Vereinswebseite für **www.sv-obermumpf.com**, veröffentlicht über GitHub Pages. Statisches HTML, CSS und wenig JavaScript, ohne Build-Schritt, externe Schriftarten oder Tracking. Die veröffentlichbaren Dateien liegen ausschliesslich in `public/`.

## Lokal ansehen

```sh
python3 -m http.server 4173 --bind 127.0.0.1 --directory public
```

Danach http://127.0.0.1:4173 öffnen. Navigation und Kerninhalte sind ohne JavaScript nutzbar; mit JavaScript gibt es auf kleinen Bildschirmen ein aufklappbares Menü. Die Vorschau ist an die lokale Loopback-Adresse gebunden.

Die lokale Abnahme umfasst alle Seiten sowie den vollständigen Statuten-Download. **Vor der ausdrücklichen Freigabe des Vereinsverantwortlichen weder pushen noch einen Pull Request erstellen oder veröffentlichen.** Private Entwürfe und die konkrete Abnahmecheckliste liegen bei Bedarf in `.local-review/`; der Ordner ist ignoriert und darf nicht eingecheckt werden.

## Inhalte bearbeiten

- `public/index.html`: Startseite mit Leitbild, nächsten Anlässen und Übersicht. Die bisherigen Anker `#verein`, `#termine`, `#fluhschiessen` und `#kontakt` bleiben erreichbar.
- `public/verein.html`: Vereinszweck, konkrete Angebote, Organisation, UID und Statuten-Download.
- `public/statuten.html`: Vollständige historische Online-Textfassung mit Inhaltsverzeichnis, Artikelüberschriften und semantischen Tabellen.
- `public/termine.html`: Bestätigte kommende Termine und getrennt gekennzeichnete vergangene Anlässe.
- `public/fluhschiessen.html`: Veranstaltungsseite mit bestätigten Schiesszeiten und Rückblick.
- `public/kontakt.html`: Vereinskontakt, Standort, Postadresse, externe Anfahrt und Partnerlinks.
- `public/styles.css`: Farben, Schriftgrössen und responsive Gestaltung.
- `public/impressum.html` und `public/datenschutz.html`: Betreiberangaben und tatsächliche Datenbearbeitung beim Hosting und bei Kontaktanfragen.
- `public/downloads/statuten-und-anhang.pdf`: Durchsuchbare historische Textfassung der vollständigen Statuten und ihres Anhangs, ausdrücklich ohne aktuellen Stand.
- `public/sitemap.xml`, `public/robots.txt` und `public/404.html`: Auffindbarkeit und Fehlerseite.

Alle HTML-Seiten verwenden dieselbe Navigation und denselben Footer direkt im Quelltext; dies benötigt keinen Generator oder Build. Änderungen an gemeinsamen Links auf allen neun Seiten nachführen. Auf der Fehlerseite sind Links ab der Domainwurzel angegeben, damit sie auch bei nicht vorhandenen verschachtelten Pfaden funktionieren.

Termine sind ausdrücklich einem Jahr zugeordnet und werden nicht automatisch aktualisiert. Beim Jahreswechsel mit dem aktuellen Vereinskalender ersetzen. Neue Termine mit maschinenlesbarem `datetime="JJJJ-MM-TT"` eintragen; vergangene Anlässe aus dem Ausblick in den Rückblick verschieben. Die Startseite zeigt nur eine Auswahl der kommenden Anlässe. Trainings- und Kursangebote nur mit bestätigtem Programm ankündigen.

Organisationsdaten: **Schiessverein Obermumpf**, UID **CHE-113.566.004**, Sitz Obermumpf. Im UID-Register lautet der Name «Schiessverein». Standort: Hauptstrasse 422, 4324 Obermumpf; Briefpost: Postfach 23, 4324 Obermumpf. Die UID ist kein Nachweis einer Steuerbefreiung. Den Kontakt `v.anderegg@sv-obermumpf.com` konsistent halten.

Das Zielscheiben-Signet und die Landschaften sind neue SVG-Gestaltungsentwürfe, keine dokumentarischen Ortsansichten. Der Vereins-Schriftzug im Footer liegt unter `public/assets/vereinslogo.png`.

## Statuten aktuell halten

1. Den Status einer Fassung vorab festlegen: Eine als aktuell angebotene Fassung muss vom Verein bestätigt sein; Beschlussdatum und Änderungen sind zu prüfen. Eine ausdrücklich gewünschte historische Fassung darf als Archivdokument bereitgestellt werden, wenn ihr fehlender aktueller Stand und bekannte Lücken direkt beim Download sowie im Dokument klar erkennbar sind. Ein offenes Datum nicht erfinden oder eine Archivfassung als aktuell ausgeben.
2. Das private Original unverändert aufbewahren. Nur die ausdrücklich freigegebene Webfassung in `public/downloads/statuten-und-anhang.pdf` ersetzen. Keine Protokolle, Mitgliedsbestätigungen oder sonstigen privaten Belege mitkopieren.
3. Bei einem Neusatz den Wortlaut vollständig gegen die beschlossene Vorlage prüfen: Artikel und Unterpunkte, Zahlen, Mehrheiten, Fristen, Beiträge, sichtbare Streichungen und Datumsangaben. Die Textquelle liegt in `documents/statuten.json`; das eingebundene Vereinslogo in `documents/assets/vereinslogo.png`. Artikel und Tabellen bleiben beim Neusatz zusammen, Seitenumbrüche können vom Scan abweichen. Den Anhang nicht stillschweigend weglassen oder eigenmächtig korrigieren.
4. Downloadhinweis auf der Vereinsseite (Seitenzahl, Grösse, Stand) sowie Zweckbeschreibung und Organisationsangaben mitprüfen. Historische Unterschriftsfunktionen im Scan sind kein aktuelles Vorstandsverzeichnis.
5. Lokal abnehmen, danach den geschützten PR-Ablauf verwenden.

Die Generatoren für die Text-PDF und die gleichwertige Online-Textfassung werden ausschliesslich lokal aufbewahrt und sind nicht Bestandteil dieses Repositorys. Bei Änderungen beide Fassungen aus der überprüften Textquelle gemeinsam aktualisieren; bei Änderungen am gemeinsamen Kopf- oder Fussbereich auch die HTML-Fassung nachführen. Die verwendeten Schriften müssen in die PDF eingebettet sein. Anschliessend jede Seite rendern und visuell prüfen sowie per Textextraktion bestätigen, dass alle Artikel und Tabellen vollständig enthalten sind. Dieser separate Dokumenten-Schritt ist kein Webseiten-Build; GitHub Pages veröffentlicht weiterhin die fertigen Dateien aus `public/`.

Die Textfassung kennzeichnet sich als Neusatz nach Scan, übernimmt historische Namensangaben ohne neue Unterschriften und dokumentiert das im Ausgangsscan offene Anhangdatum. Nach ausdrücklicher Entscheidung des Vereins wird diese Fassung als historische Information angeboten, mit dem Hinweis «nicht aktueller Stand» auf der Webseite, am Anfang der PDF und in jeder Seitenfusszeile. Das unvollständige Anhangdatum bleibt dokumentiert. Auskunft zu aktuell geltenden Bestimmungen erteilt der Verein über die Kontaktadresse. Für eine spätere aktuelle Fassung sind Beschlussdatum und Inhalt zu bestätigen. Eine neue Formatierung ist kein neuer Vereinsbeschluss.

## Barrierefreiheit prüfen

Die Umsetzung orientiert sich an WCAG 2.2 AA; eine vollständige Konformität wird nicht zugesichert. Die historischen Statuten sind über eine vollständige HTML-Alternative mit Inhaltsverzeichnis, direkt anspringbaren Artikeln, Listen und Tabellen mit Zeilen- und Spaltenüberschriften zugänglich. Streichungen werden für Vorleseprogramme eigens angekündigt. Die PDF bleibt ein zusätzlicher Download und ist weiterhin keine getaggte PDF.

Nach Layout- oder Inhaltsänderungen alle neun Seiten bei 320 CSS-Pixeln Breite und in Desktopansicht prüfen. Textgrösse auf 200 % erhöhen und benutzerdefinierte Textabstände testen: Zeilenhöhe 1,5, Absatzabstand 2 em, Zeichenabstand 0,12 em und Wortabstand 0,16 em. Inhalte und Bedienelemente dürfen nicht abgeschnitten oder überlagert werden. Schriftgrössen verwenden relative Einheiten; lange Wörter und E-Mail-Adressen dürfen umbrechen. Fokusmarkierungen müssen auf hellen und grünen Flächen sichtbar bleiben.

Mit der Tastatur Sprunglink, Hauptnavigation, Menü (Enter/Escape), Statuten-Inhaltsverzeichnis und alle Links bedienen. Automatisierte Prüfungen ergänzen die Kontrolle, ersetzen aber keinen praktischen Test mit Screenreader (zum Beispiel VoiceOver oder NVDA). Den tatsächlich geprüften Umfang und verbleibende Grenzen dokumentieren; lokale Prüfberichte bleiben in `.local-review/`.

## Vor Fotos oder Ranglisten

- Zweck, Umfang und Empfängerkreis der Veröffentlichung vorab festlegen; nur erforderliche Personendaten veröffentlichen.
- Teilnehmende rechtzeitig und verständlich informieren. Eine pauschale «Teilnahme gilt als Einwilligung»-Klausel ersetzt keine Prüfung der zulässigen Grundlage.
- Bildrechte und gegebenenfalls freiwillige, informierte Freigaben prüfen; bei Minderjährigen auch die Erziehungsberechtigten einbeziehen. Für Quellen und Freigaben interne Nachweise führen, nicht im öffentlichen Repository.
- Veröffentlichung und Entfernung/Widerspruch organisatorisch regeln, alte Inhalte regelmässig prüfen. Keine Mitgliederlisten oder privaten Kontaktdaten online stellen.
- Vor neuen Formularen, Analysewerkzeugen, Einbettungen oder anderen Diensten die Datenschutzhinweise und gegebenenfalls Einwilligungen neu prüfen.

## Auf GitHub Pages veröffentlichen

1. Auf einem lokalen `codex/`-Branch arbeiten und alle Seiten samt Statuten-PDF lokal prüfen lassen. Erst nach ausdrücklicher lokaler Freigabe den Branch mit einem Conventional Commit pushen und einen Pull Request gegen `main` erstellen.
2. CodeQL und sämtliche vorgeschriebenen Prüfungen ausführen lassen, offene Review-Konversationen klären und den Pull Request prüfen. Direkte Pushes auf `main`, Force-Pushes und das Löschen von `main` sind gesperrt; Schutzregeln nicht umgehen.
3. Nach freigegebenem Merge startet der Workflow **Vereinswebseite veröffentlichen** automatisch. Die Veröffentlichung erfolgt nur aus `main` in die Umgebung `github-pages`; Actions bleiben auf feste Commit-SHAs gepinnt.
4. Der Workflow lädt ausschliesslich `public/` hoch. Den erfolgreichen Lauf und anschliessend Seiten, Navigation, Rechtslinks und PDF unter **https://www.sv-obermumpf.com/** prüfen.

GitHub Pages verwendet `.github/workflows/pages.yml`; die Source ist in den [Pages-Einstellungen](https://github.com/sv-obermumpf/sv-obermumpf/settings/pages) auf **GitHub Actions** gesetzt. Die benutzerdefinierte Domain ist `www.sv-obermumpf.com`, HTTPS wird erzwungen. Die folgenden DNS-Angaben dokumentieren die Einrichtung und sind keine Anweisung, bestehende funktionierende Einträge erneut zu ändern.

## sv-obermumpf.com verbinden

Wenn die Domain ursprünglich bei **Google Domains** registriert wurde, wird sie inzwischen bei **Squarespace Domains** verwaltet. Google Workspace als E-Mail-Dienst ist davon zu unterscheiden. Zuerst im tatsächlichen Domainkonto den DNS-Anbieter prüfen.

1. In den GitHub-Einstellungen der Organisation `sv-obermumpf` unter **Pages** die Domain verifizieren. Den von GitHub angezeigten TXT-Eintrag beim DNS-Anbieter setzen und bestehen lassen.
2. Im Repository unter **Settings → Pages → Custom domain** `www.sv-obermumpf.com` speichern.
3. Für die Domain diese DNS-Einträge setzen:

| Typ | Name | Ziel |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | sv-obermumpf.github.io |

Nur kollidierende Webhosting-Einträge für `@` und `www` ersetzen. Vorhandene E-Mail-Einträge (MX, SPF, DKIM, DMARC) erhalten, damit die Vereinsmail weiterhin funktioniert. Falls AAAA-Einträge vorhanden sind, gemäss GitHub-Dokumentation auf die passenden Pages-IPv6-Adressen umstellen oder veraltete entfernen.

4. Nach erfolgreicher DNS-Prüfung und Zertifikatsausstellung **Enforce HTTPS** aktivieren. Die Umstellung kann bis zu 24 Stunden dauern.
5. Beide Varianten (`https://sv-obermumpf.com` und `https://www.sv-obermumpf.com`) sowie Unterseiten testen.
6. Fehlerseite, kanonische URLs, Sitemap und Datenschutzhinweise müssen zur tatsächlich verwendeten Domain und zum aktiven Hosting passen.

Bei der Veröffentlichung über GitHub Actions wird die Domain in den Pages-Einstellungen konfiguriert; eine CNAME-Datei ist dabei nicht erforderlich.

### fluhschiessen.ch

Der Anlass hat eine vollständige eigene Seite unter **https://www.sv-obermumpf.com/fluhschiessen.html**. Der aktuelle Betrieb der zusätzlichen Domain ist unbestätigt; sie wird deshalb nicht als notwendiger Navigationsweg verwendet. Es wurden keine DNS- oder Weiterleitungsänderungen vorgenommen.

Wenn die Domain künftig auf diese Vereinsseite führen soll, lässt sich beim Domainanbieter eine HTTPS-fähige Weiterleitung zu `https://www.sv-obermumpf.com/fluhschiessen.html` einrichten. Vorher klären, ob bestehende Fluhschiessen-Inhalte erhalten bleiben sollen. GitHub Pages bietet pro Site nur eine benutzerdefinierte Domain (mit passender www-Variante); zwei unabhängige Domains gehören nicht gemeinsam in die Pages-Domaineinstellung.

## Technische Quellen

- [GitHub: eigene Pages-Workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [GitHub: eigene Domain konfigurieren](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub: HTTPS und DNS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)
- [Squarespace: Migration von Google Domains](https://support.squarespace.com/hc/en-us/articles/17131164996365-About-the-Google-Domains-migration-to-Squarespace)

## Öffentliche Inhalte

Dieses Repository einschliesslich seiner Commit-Historie ist öffentlich. Nur freigegebene Website-Inhalte einchecken. Interne Vereinsunterlagen, Mitgliederlisten, Sitzungsprotokolle, Zugangsdaten und lokale Recherche-Notizen gehören nicht in dieses Repository.
