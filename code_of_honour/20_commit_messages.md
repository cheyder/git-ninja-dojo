# Commit Messages

## TLDR;

Eine Commit Message besteht aus einem kurzen Subject, dass das Ziel der Änderung zusammenfasst und einem Body der inhaltliche und fachliche Details der Änderung dokumentiert.

## Form

>[!IMPORTANT]
> - sind in der Sprache verfasst, auf die sich mein Team geeinigt hat
> - beginnen mit einem Großbuchstaben
> - haben ein Subject, das
>   - die Zielsetzung der Änderung zusammenfasst, nicht die technische Anpassung
>   - im Imperativ verfasst ist (`Add foo` statt `Added foo`)
>   - nicht länger als 72 Zeichen ist
>   - keinen Punkt am Ende hat
>   - durch eine Leerzeile vom Body getrennt ist
> - haben einen Body, der
>   - Fließtext nach 72 Zeichen umbricht
>   - erst das vorhandene Problem/die Änderung beschreibt
>   - dann die Lösung zusammenfasst

### Hintergründe

Den Betreff der Commit Message im **Imperativ** zu schreiben ist Git-Standard. Alle Commits die durch Git-Befehle angelegt werden (`git merge`, `git revert` etc.) verwenden ihn: `Merge pull request #number from <branch>` oder `Revert "<commit>"`. Die Idee dahinter ist, dass sofort klar ist, was sich durch diesen Commit im Code ändert. Eine häufig verwendete Formel zu Verdeutlichung ist, dass eine Commit Message folgenden Satz ergänzen soll: If applied, this commit will...

Dass immer eine Leerzeile zwischen Subject und Body steht, ist von Git vorgegeben. Bis zur ersten Leerzeile wird alles als Subject behandelt. Das heißt, wird sie vergessen, steht auf einmal alles im Subject und Befehle wie `git log --oneline` oder `git shortlog` werden unübersichtlich und können im schlimmsten Fall nicht mehr sinnvoll verwendet werden – was gleichzeitig der Grund ist, dass Subjects auf 72 Zeichen begrenzt sind.

## Inhalt

>[!IMPORTANT]
>```
>Name the effect/goal of the changes in the subject
>
>Describe the situation before: The false behaviour and its cause. How
>to reproduce the issue. Or provide helpful context informations for
>the new feature.
>
>Summarize the change and describe how it leads to the desired result. 
>If there have been other possible solutions, document your decision.
>```

Außerdem können hilfreiche Zusatzinformationen hinzugefügt werden:

- Commit-IDs von Commits die mit diesem in Zusammenhang stehen
- Links zu Dokumentationen
- Links zu Issues bei GitHub
- Ticketnummer

### Beispiel

Zum Vergleich ein Beispiel für Commit Messages die jeweils den gleichen imaginativen Commit beschreiben:

```
Fix import bug
```
vs.
```
Fix crash of CSV-Import when customer has no first name

The CSV import always replaces empty strings with null values, and this
causes a crash later on because the customer must have a string as their
first name.

Adjusting the CSV import to keep empty string would need lots of
adjustments and we must also support data sets that don't contain first
names at all. So it seems prudent to convert null values to empty
strings when assigning the value to the customer.  Note that we can't
simply ignore null values, because we might be updating an existing
customer and must not keep the previous value!
```

Mit der ersten Commit Message fehlen meinen Reviewer:innen quasi alle Informationen die sie benötigen, um das Problem einzuordnen, nachzustellen oder die Lösung beurteilen zu können. In der zweiten Commit Message ist klar welcher Import betroffen ist (ggf. gibt es mehrere), mit welchen Daten das Problem ausgelöst werden kann, warum das Problem auftritt, für welche Lösung ich mich entschieden habe, warum ich dies tat, und weshalb ich eine andere mögliche Lösung, die einer Reviewer:in evtl. auch eingefallen wäre, verworfen habe.

Mit der Commit Message allein hat der Reviewer hier schon alle Informationen, die ich mir als Entwickler:in evtl. langwierig erarbeiten musste, und kann den prinzipiellen Lösungsansatz hoffentlich schon allein damit beurteilen. Im Code muss dann "nur" noch geschaut werden, ob diese Lösung auch wirklich umgesetzt wurde und korrekt und vollständig ist.
