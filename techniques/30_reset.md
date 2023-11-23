# Wiederherstellen

| Command                      |                                                                            |
|------------------------------|----------------------------------------------------------------------------|
| `git reflog`                 | Der Blick ins Git des Git                                                  |
| `git reset --soft <Commit>`  | Gehe zurück zu <Commit>, behalte alles, dort wo es war.                    |
| `git reset --mixed <Commit>` | Gehe zurück zu <Commit>, uncommitte und unstage alle Änderungen bis dahin. |
| `git reset --hard <Commit>`  | Gehe zurück zu <Commit>, verwerfe alles bis dahin.                         |