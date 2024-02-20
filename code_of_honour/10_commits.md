# Commits

## TLDR;

Ich strukturiere meine Commits so, dass ich anderen die Arbeit mit meinem Code (inkl. mir selbst!) erleichtere. Alle meine Commits sind vollständig, lauffähig, minimal und informativ.

## vollständig

> [!IMPORTANT]
> Änderungen sind mit all ihren Abhängigkeiten in einem Commit zusammengefasst und nicht über mehrere Commits verteilt.

Gerade wenn ich einen größeren PR erstelle, kann ich anderen in der Code-Review helfen, nicht von der Komplexität erschlagen zu werden, in dem ich meine Änderungen in einzeln reviewbare Commits aufteile. Das funktioniert nur, wenn alle Bestandteile der Änderung im jeweiligen Commit vorhanden sind. Wenn ich zum Beispiel nur ein Interface erweitere, aber die neue Methode nicht verwende und/oder nicht in den entsprechenden Klassen implementiere, sind spätere Leser:innen des Codes darauf angewiesen sich die Einzelteile zusammenzusuchen, was mehr Aufwand bedeutet und die Gefahr birgt etwas zu übersehen.

Weitere Beispiele für Dinge die in der Regel zusammengehören:
- Migrationen und Modellanpassungen
- Bugfix + Regressionstest
- Neues Feature + Tests
- Funktionsanpassungen + Tests

## lauffähig

> [!IMPORTANT]
> Alle Tests, Checks, Migrationen laufen durch.

Wenn ich meine Änderungen in einzelne, vollständige Commits aufteile, dabei aber Fehler, die ich eventuell mit einem Commit eingebaut habe, erst mit einem späteren Commit behebe, erschwert das die Review. Andere können dann zwar große PRs Commit für Commit durchsehen, sie schreiben dann aber Kommentare für Fehler, die schon längst behoben sind. Mal ganz abgesehen davon, dass Commits in der Art von `Apply PR feedback`, das Prinzip der Vollständigkeit untergraben: Ein Commit, der nicht alle Checks besteht, ist nicht vollständig.

Ein weiterer Aspekt hier sind Tools wie `git bisect` mit denen ich bestimmen kann in welchem Commit ein Bug entstanden ist. Um so mehr Commits nicht eigenständig lauffähig sind, um so weniger exakt kann ich die Entstehung eingrenzen, und um so weniger nützlich werden solche Werkzeuge.


## minimal
> [!IMPORTANT]
> Änderungen, die nicht zwingend zusammengehören fließen in separate Commits.

Das Gegenstück zur Vollständigkeit ist die Minimalität eines Commits. Jede Änderung die unnötig in einen Commit mit aufgenommen wird, erhöht dessen Komplexität. Zum Einen müssen sich Reviewer:innen erstmal erarbeiten, welche Teile denn interagieren und welche unabhängig voneinander sind, zum Anderen ist dadurch auch das Lesen der Änderungen aufwendiger, weil Zusammenhänge nur durch häufiges Hin- und Herspringen im Diff nachvollzogen werden können.

Weitere relevante Aspekte sind Tools wie `git revert` um z.B. Änderungen rückgängig zu machen. Code Style Fixes und eine fehlerhafte Änderung sind zusammen in einem Commit gelandet? `git revert` dreht beides zurück. Wären die Style Fixes einmal vorab gemacht worden, könnte man die fehlerhafte Änderung einzeln reverten, ohne den Coding Style wieder kaputt zu machen oder das ganze manuell zu machen.

## informativ

> [!IMPORTANT]
> Die Commit-Message enthält die Auswirkung der Änderung, eine Beschreibung des Zustands davor, und eine Zusammenfassung der Änderung.

Neben den strukturellen Informationen (Zusammenhänge, Aufbau, Abhängigkeiten), die mir die Aufteilung der Commits vermittelt, habe ich mir während der Entwicklung oft auch fachliche und technische Informationen oder Entscheidungen erarbeitet, die für meine Reviewer:innen nützlich bis unabdingbar sind. Ein guter Platz dafür ist die Commit Message, denn die Bündelung von Änderung und deren Dokumentation hat einige Vorteile gegenüber Kommentaren im Code oder externen Systemen. Eine Commit Message

- ist unmittelbar vom Code aus auffindbar (`git blame`, `git log`, etc.)
- wird beim commitweisen Reviewen über dem Diff angezeigt
- ist spezifisch für die Änderung
- bezieht sich auf eine Version und kann demnach nicht veralten, im Gegenteil, sie
- bildet mit den anderen den historischen Verlauf der Änderungen ab

Eine gute Commit Message ist dabei schnell verständlich und orientiert sich deshalb immer an derselben [Grundform](20_commit_messages.md).
