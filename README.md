# Git Ninja Dojo

Willkommen im Git Ninja Dojo! Hier lernst du die Git Commit-Kunst – Commit für Commit, ist ja klar. Für alle, die mehr wollen als `Strg+S` mit wahllosen Dateinamen. Für alle, die ihre Codebase verstehen wollen. Für alle, die große PRs in kleinen, sinnvollen Einheiten durchsehen wollen.

## Ehrenkodex (Konventionen)

### Commits sind sinnvolle, zusammenhängende und voll funktionsfähige Einheiten

- [ ] alle Tests und Checks laufen durch
- [ ] alles, was für diese eine Änderung relevant ist, ist in diesem Commit
- [ ] die Commit Message enthält das Ziel der Änderung, eine Beschreibung des Zustands davor, und eine Zusammenfassung der Änderung
- [ ] wenn Anpassungen voneinander unabhängig lauffähig sind und für sich Sinn ergeben, kommen sie in eigene Commits

#### Beispiele

- Tests gehören in den Commit, in dem der Code geschrieben wurde, den er testet (außer sie werden nachträglich hinzugefügt)
- die Migration und die Änderungen an der Entity gehören in denselben Commit
- Hinzufügen und Entfernen von Paketen/Bibliotheken kann in der Regel in einen eigenen Commit
- Renaming und jedes für sich funktionsfähige Refactoring kommt in einen eigenen Commit
- "typo fixed" gibt es nicht mehr
- "aktueller Stand" gilt ab sofort als ehrenlos

### Commit Messages haben ein Subject und einen Body

- [ ] Commit Messages werden in Englisch geschrieben
- [ ] Schreibe den ersten Buchstaben des Subjects groß
- [ ] Die Subject-Line hat keinen Punkt am Ende
- [ ] Soft-limit für das Subject sind 50 Zeichen, Hard-Limit 72 Zeichen
- [ ] Hard-Limit für den Body sind 72 Zeichen
- [ ] Schreibe das Subject im Imperativ
- [ ] Benutze überall Präsens
- [ ] Beschreibe im Subject das Ziel der Änderung, nicht die Änderung
- [ ] Füge zwischen Subject und Body eine Leerzeile ein
- [ ] Füge zwischen den Absätzen im Body eine Leerzeile ein
- [ ] Beschreibe im ersten Absatz den aktuellen Zustand und das Problem mit ihm, bzw. die Anforderung an ihn
- [ ] Fasse im zweiten Absatz die Änderung/die Lösung zusammen
- [ ] Füge hilfreiche, zusätzliche Informationen wie Links zu Dokumentationen oder Issues bei GitHub danach ein
- [ ] Füge als Letztes die Ticketnummer hinzu

__TODO: Konfiguration von PHPSTORM (evtl. weitere IDEs?)__

### Branches

Vor dem ersten Push können wir mit der Commit History machen, was wir wollen.
Nach dem ersten Push können wir die Commit History nur noch ändern, wenn wir alleine auf dem Branch arbeiten oder uns sehr eng mit allen Beteiligten absprechen.
Nach dem Merge in den Main-Branch wird nichts mehr an der Commit History geändert!


## Moves (CheatSheet)

### Understand
| Command       |                                   | 
|---------------|-----------------------------------|
| `git log`     | Commit History anzeigen           |
| `git blame`   | Wer hat was in der Datei geändert |

### Rearrange
| Command                                            |                                                                                                         |
|----------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `git stash`                                        | Alle nicht committeten Änderungen beiseite legen                                                        |
| `git stash pop`                                    | Den letzten Eintrag im Stash hervorholen                                                                |
| `git stash list`                                   | Alle Einträge im Stash sehen                                                                            |
| `git stash --keep-index`                           | Alle nicht committeten Änderungen beiseite legen, aber Staging Area behalten                            |
| `git commit --amend`                               | Änderung in der Staging Area zum letzten Commit hinzufügen                                              |
| `git rebase master`                                | Den Unterschied zwischen dem aktuellen Branch und master, an master dranhängen.                         |
| `git rebase --onto <Branch> HEAD~<Anzahl Commits>` | Die letzten <Anzahl Commits> auf dem aktuellen Branch nehmen und an <Branch> dranhängen.                |
| `git rebase -i HEAD~<Anzahl Commits>`              | Interaktives Rebase der letzten <Anzahl Commits> auf dem aktuellen Branch.                              |
| `git push --force-with-lease`                      | Erneutes pushen nach einem Rebase, ohne mögliche Änderungen im Repo zu überschreiben.                   |
| `git pull --rebase`                                | Den Remote-Branch pulln, nachdem er gerebased wurde.                                                    |
| `composer update --lock`                           | Nur den Hash in `composer.lock` updaten, wenn unterschiedliche `composer.json` Dateien gemerged werden. |

### Reset
| Command                      |                                                                            |
|------------------------------|----------------------------------------------------------------------------|
| `git reflog`                 | Der Blick ins Git des Git                                                  |
| `git reset --soft <Commit>`  | Gehe zurück zu <Commit>, behalte alles, dort wo es war.                    |
| `git reset --mixed <Commit>` | Gehe zurück zu <Commit>, uncommitte und unstage alle Änderungen bis dahin. |
| `git reset --hard <Commit>`  | Gehe zurück zu <Commit>, verwerfe alles bis dahin.                         |


## Kombos (Übungen)

__TODO: auf einem Branch einen fehlgeschlagenen Rebase commiten, in dem vielleicht drei Commits gesquashed wurden und folgende Szenarien nacheinander durchgespielt werden können__

1. undo a completed but failed rebase with reflog
2. reset last commit and distribute its files over the remaining commits
3. solve a composer.json merge conflict on the way (update --lock)
4. push again 

__TODO: zweiter Branch der von erstem abzweigt__

1. update a branch that depends on a branch which was updated/rebased

__TODO: dritter Branch mit mehreren Commits, die eine kurze Geschichte erzählen, aber in jedem Commit nur ein Teil steht, im letzten Commit nur das Ende enthalten ist__

1. die Vorzüge von git blame wenn es tatsächlich eine Commit History gibt
2. (vielleicht auch in dem Stil PRs Commit für Commit durchzusehen?)
