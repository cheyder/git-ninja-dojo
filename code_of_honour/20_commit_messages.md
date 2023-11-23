# Commit Messages

## TLDR;

>[!IMPORTANT]
> - sind in der Sprache verfasst, auf die sich mein Team geeinigt hat
> - beginnen mit einem Großbuchstaben
> - haben ein Subject, das
    >   - nicht mit einem Punkt endet
>   - nicht länger als 50 und auf keinen Fall länger als 72 Zeichen ist
>   - im Imperativ verfasst ist
>   - das Ziel/den Effekt der Änderung beschreibt, nicht die technische Anpassung
> - haben einen Body, der
    >   - nie längera ls 72 Zeichen ist
>   - erst das vorhande Problem beschreibt
>   - dann die Lösung zusammenfasst
>   - ggf. hilfreiche Zusatzinformationen enthält:
      >     - Commit-IDs von Commits die mit diesem in Zusammenhang stehen
>     - Links zu Dokumentationen
>     - Links zu Issues bei GitHub
> - haben eine Leerzeile zwischen
    >   - Subject und Body
>   - jedem Absatz im Body
> - enthalten in der letzten Zeile die Ticketnummer

## 1. Grad: Einordung
```
Bugfix
Typo
Fix unit test
```

Es gibt Commit-Messages, die ihren Commit erstmal nur einer Kategorie zuordnen und nichts weiter. Sie haben keinen wirklichen Nutzen, außer dass überhaupt Versionierung verwendet wird.

## 2. Grad: Verortung
```
Add <feature> to <class>
Remove <feature> from <class>
Move <part> to <another place>
```

Die vermutlich gängigste Form von Commits, die schon etwas informativer sind, verorten die technische Änderung. Dass sie sagen, wo etwas geändert wurde, ist meist weniger interessant, als dass sie sagen, was dort geändert wurde.

## 3.  Grad: Auswirkung
```
Receive always the same email when fetching by UID
```

Idealerweise sagt mir das Subject einer Commit-Message nichts darüber, was technisch geändert wurde, sondern welchen Effekt die Änderung hat, bzw. haben soll.

## 4. Grad: Body
```
Receive always the same email when fetching by UID

Sometimes we try to fetch an email via imap from the users mailbox and
don't receive the correct one, but another one. The reason is that
fetching an email with its UID is error prone as the UID only MUST not
change during a session, but may change between session, which MUST be
detectable by comparing the UIDVALIDITY.

To prevent that, the UID is always used/persisted with its UIDVALIDITY
and when fetching the next time by UID, the corresponding UIDVALIDITY
is checked against the current one on server side. If they differ, the
UID has to be fetched again.

RFC: https://datatracker.ietf.org/doc/html/rfc9051#name-message-numbers

```

Ich sehe nicht nur auf den ersten Blick anhand des Subjects, welchen Effekt dieser PR hat, sondern wenn ich mir den Body ansehe, erfahre ich sogar warum diese neue Variable `UIDVALIDITY` hinzugefügt wurde, wie sie mit dem von uns genutzten Protokoll zusammenhängt und wo ich ggf. weiterführende Infos finde.

Stell dir vor, so würden alle Commit Messages aussehen. Stell dir vor, du musst mal wieder an den Legacy Core deiner Company und es ist zwar immer noch alles historisch gewachsen, aber überall steht dran, warum das so ist, wie es dazu kam und in den Commits siehst du alle Stelle, die damit zusammenhängen. 