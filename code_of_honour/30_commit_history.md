# Commit History

Damit unsere Commits immer vollständig sind und wir am Ende einer Code-Review nur den aktuellsten Stand unserer minimalen, lauffähigen und informativen Commits mergen können, müssen wir während der Entwicklung und der Nacharbeit die vorhandene Commit History nachträglich ändern: Dateien in Commits anpassen, hinzufügen, entfernen, oder die Commit Message neu schreiben. Dieser Vorgang heißt in Git Rebasing.

**Rebasing** kann anfangs etwas ungewohnt sein, insbesondere wenn ich Git bisher eher unter folgendem Credo verwendet habe: "Commite so oft und so viel und so kleinschrittig wie es geht und ändere auf keinen Fall die History, sonst geht die Welt unter!" 

Ja, mit Rebasing lässt sich viel kaputt machen, aber im Grunde lässt sich auch alles rückgängig machen. Nur die folgenden drei Regeln solltest du immer beachten:

1. Vor dem ersten Push kann ich mit der Commit History machen, was ich will.
2. Nach dem ersten Push kann ich die Commit History nur noch ändern, wenn ich alleine auf dem Branch arbeite oder mich sehr eng mit allen Beteiligten abspreche.
3. Nach dem Merge in den Main-Branch wird nichts mehr an der Commit History geändert!