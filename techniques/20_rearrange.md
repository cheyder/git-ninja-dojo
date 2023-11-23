# Umstrukturieren

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