# Ideen

- Anleitungen für IDE Konfiguration bereitstellen
  - editorconfig?
  - PHPSTORM
  - VSCODE
  - VIM


## Training

__auf einem Branch einen fehlgeschlagenen Rebase commiten, in dem vielleicht drei Commits gesquashed wurden und folgende Szenarien nacheinander durchgespielt werden können__

1. undo a completed but failed rebase with reflog
2. reset last commit and distribute its files over the remaining commits
3. solve a composer.json merge conflict on the way (update --lock)
4. push again

__zweiter Branch der von erstem abzweigt__

1. update a branch that depends on a branch which was updated/rebased

__dritter Branch mit mehreren Commits, die eine kurze Geschichte erzählen, aber in jedem Commit nur ein Teil steht, im letzten Commit nur das Ende enthalten ist__

1. die Vorzüge von git blame wenn es tatsächlich eine Commit History gibt
2. (vielleicht auch in dem Stil PRs Commit für Commit durchzusehen?)
