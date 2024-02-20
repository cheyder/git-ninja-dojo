# Umstrukturieren

| Command                               |                                                                                                                 |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `git stash`                           | Alle noch nicht committeten Änderungen beiseite legen                                                           |
| `git stash pop`                       | Den letzten Eintrag aus dem Stash anwenden und aus dem Stash entfernen                                          |
| `git stash list`                      | Alle Einträge im Stash anzeigen                                                                                 |
| `git stash --keep-index`              | Alle Änderungen beiseite legen, aber alles was schon gestaged wurde, dabei nicht aus der Staging Area entfernen |
| `git commit --amend`                  | Änderung in der Staging Area zum letzten Commit hinzufügen                                                      |
| `git commit --fixup=<commit-id>`      | Erstellt einen Fixup-Commit für ein späteres Rebase                                                             |
| `git rebase <Branch>`                 | Setze alle Commits von HEAD bis zum Abzweigen von `<Branch>` auf den neuesten Commit im `<Branch>` um           |
| `git rebase --onto <Branch> HEAD~<n>` | Setze alle Commits von HEAD bis zum `<n>`ten First-Parent auf `<Branch>` um                                     |
| `git rebase -i HEAD~<n>`              | Interaktiver Rebase beginnend bei `HEAD~<n>`                                                                    |
| `git push --force-with-lease`         | Erneutes Pushen nach einem Rebase, ohne mögliche Änderungen im Repo zu überschreiben.                           |
| `git pull --rebase`                   | Den Remote-Branch pulln, nachdem er gerebased wurde.                                                            |
| `composer update --lock`              | Nur den Hash in `composer.lock` updaten, wenn unterschiedliche `composer.json` Dateien gemerged werden.         |

