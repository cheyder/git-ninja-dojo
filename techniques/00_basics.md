# Grundlagen Git

Um Git über `pull`, `branch`, `commit`, `push` hinaus zu verwenden ist es sehr hilfreich, sich mit ein paar Grundkonzepten und Begriffen vertraut zu machen. Sie werden hier eingeführt und dann im Folgenden ohne weitere Erklärung verwendet.

## Commits, Branches und weitere Pointer

Eine Version in Git, ist ein Snapshot des versionierten Verzeichnisses.

Commits sind Pointer auf diese Snapshots und enthalten außerdem ein paar Metadaten wie Name oder E-Mail-Adresse, die Commit-Message und weitere Pointer auf die vorangegangenen Commits, die sogenannten Parents.
Initiale Commits haben keine Parents, ein normaler Commit hat einen und der Commit für einen Merge aus zwei oder mehr Branches hat dementsprechend zwei oder mehr Parents.

Branches sind erstmal bloß Pointer die auf einen (!) Commit zeigen. Aber sie "wandern mit", wenn neue Commits hinzugefügt werden. Einen neuen Branch von `master` aus anzulegen (`git branch <name-of-branche>`) bedeutet nichts anderes, als zu dem Commit, auf den der Pointer `master` zeigt, einen weiteren Pointer (`<name-of-branch>`) hinzuzufügen.

Ein weiterer wichtiger Pointer ist `HEAD`, der in Git so viel bedeutet wie "Where am I?". `HEAD` zeigt in der Regel auf einen Branch, nämlich den, den ich gerade ausgecheckt habe. Ich kann aber auch einen einzelnen Commit auschecken, dann zeigt `HEAD` auf einen Commit (sogenannter "detached head state").

Von einem Branch abzuzweigen, bedeutet also im Grunde
1. dem Commit bzw. Branch, den ich aktuell ausgecheckt habe (`HEAD`) einen neuen Pointer hinzuzufügen (`feature-branch`) (branch)
2. den `HEAD`-Pointer auf `feature-branch` zu setzen (checkout)
3. der mitwandert, wenn ein neuer Commit hinzugefügt wird (commit)

Danch zeigt `master` immer noch auf den vorherigen Commit und `feature-branch` auf den neuen.

```
$ git checkout master

        HEAD
        |
        master
        | 
–C1–C2–C3

$ git branch feature-branch

        HEAD
        |
        master
        | 
–C1–C2–C3
        |
        feature-branch
        
$ git checkout feature-branch

        master
        | 
–C1–C2–C3
        |
        feature-branch
        |
        HEAD
        
$ git commit

        master
        | 
–C1–C2–C3–C4
           |
           feature-branch
           |
           HEAD
```

## Navigation

Es gibt verschiedene Wege in Git Commands anzugeben, wo ich hin möchte. Am Häufigsten werden die Pointer verwendet, die wir gerade kennengelernt haben (Commit, Branch, HEAD). Etwas dynamischer wird es mit den beiden Suffixen `^` und `~`.

### ~

In der Regel wird die Tilde (`~`) genutzt um von einem Punkt, zum Beispiel HEAD, eine bestimmte Anzahl von Generationen zurückzugehen. Dabei **wird aber immer nur der erste Parent berücksichtigt**, d.h. bei Merge-Commits werden die anderen Parents außer Acht gelassen. Aber für die meisten Anwendungsfälle ist die Tilde völlig ausreichend, den mit ihr gehe ich sozusagen auf möglich direkten Wege in zurück. 

### ^

Das Zirkumflex, Dach oder Caret macht im Endeffekt das Gleiche, aber mit ihm ist es möglich in Merge-Commits auch die anderen Parents anzusteuern, sozusagen beim Zurückgehen abzubiegen.

```
D   E
 \ /
  B   C
   \ /
    A

A = A^0
B = A^1 = A^ = A~1
C = A^2
D = A^^ = A^1^1 = A~2
E = A^^2
```