# Schiessverein Obermumpf

Statische Vereinswebseite für **sv-obermumpf.com**, veröffentlicht über GitHub Pages. HTML, CSS und wenig JavaScript, ohne Build-Schritt, externe Schriftarten oder Tracking. Die veröffentlichbaren Dateien liegen ausschliesslich in `public/`.

## Lokal ansehen

```sh
python3 -m http.server 4173 --bind 127.0.0.1 --directory public
```

Danach http://127.0.0.1:4173 öffnen. Die Startseite funktioniert auch direkt als Datei und ohne JavaScript; mit JavaScript gibt es auf kleinen Bildschirmen ein aufklappbares Menü.

## Inhalte bearbeiten

- `public/index.html`: Vereinsvorstellung, Termine, Fluhschiessen und Vereinskontakt.
- `public/styles.css`: Farben, Schriftgrössen und responsive Gestaltung.
- `public/impressum.html`: Kontakt für die Webseite, **Valentin Anderegg**, `v.anderegg@sv-obermumpf.com`.
- `public/datenschutz.html`: Angaben zur technischen Umsetzung und zum Hosting.

Termine sind ausdrücklich dem Jahr 2026 zugeordnet und werden nicht automatisch aktualisiert. Beim Jahreswechsel mit dem aktuellen Vereinskalender ersetzen. Neue Termine mit maschinenlesbarem `datetime="JJJJ-MM-TT"` eintragen.

Das Zielscheiben-Signet und die Landschaften sind neue SVG-Gestaltungsentwürfe, keine dokumentarischen Ortsansichten. Der Vereins-Schriftzug im Footer liegt unter `public/assets/vereinslogo.png`.

## Auf GitHub Pages veröffentlichen

1. Dateien prüfen, committen und auf `main` pushen.
2. Im [Repository unter Settings → Pages](https://github.com/sv-obermumpf/sv-obermumpf/settings/pages) bei **Source** die Option **GitHub Actions** auswählen.
3. Unter **Actions** den Workflow **Vereinswebseite veröffentlichen** starten (oder nach der Einrichtung erneut auf `main` pushen).
4. Der Workflow lädt nur `public/` hoch. Nach erfolgreichem Durchlauf die angezeigte Pages-URL testen: zunächst voraussichtlich `https://sv-obermumpf.github.io/sv-obermumpf/`.

GitHub Pages verwendet den Workflow in `.github/workflows/pages.yml`. Die benutzerdefinierte Domain ist `www.sv-obermumpf.com`.

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
6. Den Startseitenlink in `public/404.html` nach der Domainaktivierung auf `https://sv-obermumpf.com/` ändern und den Hostingtext in `public/datenschutz.html` auf den dann aktiven Betrieb aktualisieren.

Bei der Veröffentlichung über GitHub Actions wird die Domain in den Pages-Einstellungen konfiguriert; eine CNAME-Datei ist dabei nicht erforderlich.

### fluhschiessen.ch

Der Anlass hat einen eigenen Abschnitt auf der Startseite und einen Link zur bestehenden Domain. Die Domain war während der Recherche nicht abrufbar; ihr aktueller Betrieb ist deshalb unbestätigt. Es wurden keine DNS- oder Weiterleitungsänderungen vorgenommen.

Wenn die Domain künftig auf diese Vereinsseite führen soll, lässt sich beim Domainanbieter eine HTTPS-fähige Weiterleitung zu `https://sv-obermumpf.com/#fluhschiessen` einrichten. Vorher klären, ob bestehende Fluhschiessen-Inhalte erhalten bleiben sollen. GitHub Pages bietet pro Site nur eine benutzerdefinierte Domain (mit passender www-Variante); zwei unabhängige Domains gehören nicht gemeinsam in die Pages-Domaineinstellung.

## Technische Quellen

- [GitHub: eigene Pages-Workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
- [GitHub: eigene Domain konfigurieren](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
- [GitHub: HTTPS und DNS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)
- [Squarespace: Migration von Google Domains](https://support.squarespace.com/hc/en-us/articles/17131164996365-About-the-Google-Domains-migration-to-Squarespace)

## Öffentliche Inhalte

Dieses Repository einschliesslich seiner Commit-Historie ist öffentlich. Nur freigegebene Website-Inhalte einchecken. Interne Vereinsunterlagen, Mitgliederlisten, Sitzungsprotokolle, Zugangsdaten und lokale Recherche-Notizen gehören nicht in dieses Repository.
