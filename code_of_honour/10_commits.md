# Commits

## TLDR;

Siehe die farbigen Boxen, am Anfang der Abschnitte.

## lauffähig

> [!IMPORTANT]
> Alle Tests, Checks, Migrationen laufen durch.

Ich habe ein Feature, das kaputt ist, weiß aber noch, dass es in einer früheren Version auf jeden Fall funktioniert hat. Ich möchte z.B. mit `git bisect` herausfinden, seit welchem Commit es kaputt ist. Wenn ich in der Reihe zu testender Commits, dann welche habe, die gar nicht lauffähig sind, in dem die Tests oder Checks fehlschlagen, erschwert das die Suche.

Ich schaue einen großen PR Commit für Commit durch. In einem Commit sind Anpassungen, die gar nichts mit dem Rest zu tun haben. Sie sind nur dafür da, einen Fehler, der in einem vorherigen Commit eingebaut wurde, zu beheben. Dabei könnte ich mit einem interaktiven Rebase, diesen Fix direkt in den vorherigen Commit einbauen.

## zusammenhängend

> [!IMPORTANT]
> Alles, was für diese eine Änderung relevant ist, ist in diesem Commit.

Ich muss einen Bug fixen. Die Codestelle ist schon etwas älter und nicht gerade selbsterklärend. Alle Leute, die mit `git blame` angezeigt werden, sind schon längst nicht mehr in der Firma. Du willst wissen, was es mit dieser einen Stelle auf sich hat, lässt Dir mit `Show git history for selection` alle Commits anzeigen, die mit dieser Stelle in Zusammenhang stehen. Aber in den Commits sind gar nicht alle Änderungen enthalten, die mit dem Commit `Fix this bug` in Zusammenhang stehen.

Ich sehe nicht die Tests, die diese Stelle testen. Ich sehe nicht die Migration, die nötig war, damit diese Stelle läuft. Ich sehe nicht die Anpassung, die während der Code Review noch nachgeschoben wurde, weil die Änderung sonst gar nicht den gewünschten Effekt hatte. Alle Anpassungen, die mit dieser Stelle zusammenhängen sind über mehrere Commits verteilt, deren Zusammenhänge nicht oder nur schwer nachvollziehbar.

Viel hilfreicher wäre ein einzelner Commit, in dem alles enthalten ist. Wenn ich mir die Changes dieses Commits anzeigen lasse, sehe ich auf einen Blick alle Stellen, die mit dieser Änderung/Stelle zusammenhängen. Ich kann ohne weiteres nachvollziehen, warum der Code an dieser Stelle so ist, wie er ist und wo evtl. Side-effects auftreten könnten, wenn ich hier was ändere.

Umgekehrt gilt natürlich das Gleiche: Ich öffne die Git-History für eine bestimmte Stelle im Code und lande bei einem Commit in der Art von `Simply everything which came to my mind while working on this poorly specified ticket I started working on two weeks ago – have fun and don't panic`. Jede Anpassung die für sich lauffähig und sinnvoll ist, kommt in einen eigenen Commit.

## informativ

> [!IMPORTANT]
> Die Commit-Message enthält die Auswirkung der Änderung, eine Beschreibung des Zustands davor, und eine Zusammenfassung der Änderung.

Das betrifft vor allem die Commit-Message. Ich schaue mal wieder in die Git-History mit der langsam sterbenden Hoffnung, dort irgendeine hilfreiche Information zu dieser absolut nicht nachvollziehbaren Stelle im Code zu finden. Aber ich finde:

```
Fix bug
Work in progress
Remove something
Style
Add it again
Current state
Typo
Fix unit tests
< the name of a class which can be found in this commit >
< a more or less random word, associated with the changes >
```

Was mir geholfen hätte:

```
Fix <false behaviour>
```

Ah interessant! Ich weiß sofort, was dieser Commit machen soll und vor allem, ob er für mich gerade interessant sein könnte. Wenn er das könnte, kann ich für Details auch noch in den Body schauen:

```
Fix <false behaviour>

Describe the false behaviour and its cause shortly. Describe shortly
the change and how it fixes the bug.

If there is a Commit, which introduced this bug, provide its ID
If there is a link to an issue or documentation which describes the
background of this change, add this as well

<Ticket-Number>
``` 

Alright! Das erklärt mir, warum es ausgerechnet so gelöst wurde und falls ich an der Stelle was ändern muss, weiß ich auch sofort, mit welchen anderen Stellen sie zusammenhängt. Danke Developer aus der Vergangenheit, Du hast mir gerade meine Arbeit ein Stück leichter gemacht!