# Klassenbeschreibung

## Zweck

Die Klasse dient dazu, sogenannte Mutationen, die ein `User`, ein `Administrator` in Bezug auf den Daten eines `Aliasvorschlag`s tätigen kann, zu ermöglichen. \
Dabei sind Mutationen Anfragen, die Daten verändern.

## Einschränkungen

Um die Mutation tätigen zu können, muss der Anfrager der Mutation ein entweder ein `User` oder ein `Administrator` sein (hängt von der jeweiligen Methode ab, und ist demzufolge bei jeder Methode festgelegt).

## Methoden

### addAliasVorschlag(aliasSuggestion : AliasSuggestion, mapID : MapID) : Boolean

- Einschränkung
  - Diese Methode darf nur von einem `Administrator` ausgeführt werden.
- Parameter
  - aliasSuggestion
    - der Alias-Vorschlag, der als Bezeichner für das entsprechende Kartenobjekt fungieren soll
  - mapID
    - die ID des Kartenobjekts, dessen Alias-Vorschlag hinzugefügt werden soll
- Rückgabewert
  - Boolean
    - wahr, wenn der gewünschte Alias erfolgreich hinzugefügt werden konnte, sonst falsch
- Zweck
  - ermöglicht das Hinzufügen eines Alias-Vorschlags zur Datenbank der Alias-Vorschläge auf dem Server

### setShowSuggestionStandardValPos(newStandardVal : int)

- Einschränkung
  - Diese Methode darf nur von einem `Administrator` ausgeführt werden.
- Parameter
  - newStandardVal
    - der neue Standardwert, den ein Alias-Vorschlag als Mindestanzahl positiver Bewertungen haben muss, damit der Alias-Vorschlag dem `Administrator` angezeigt wird
- Zweck
  - ermöglicht das Setzen eines neuen Standardwertes, den ein Alias-Vorschlag als Mindestanzahl positiver Bewertungen haben muss, damit der Alias-Vorschlag dem `Administrator` angezeigt wird

### setShowSuggestionStandardValNeg(newStandardVal : int)

- Einschränkung
  - Diese Methode darf nur von einem `Administrator` ausgeführt werden.
- Parameter
  - newStandardVal
    - der neue Standardwert, den ein Alias-Vorschlag als Mindestanzahl negativer Bewertungen haben muss, damit der Alias-Vorschlag dem `Administrator` angezeigt wird
- Zweck
  - ermöglicht das Setzen eines neuen Standardwertes, den ein Alias-Vorschlag als Mindestanzahl negativer Bewertungen haben muss, damit der Alias-Vorschlag dem `Administrator` angezeigt wird

## Abhängigkeiten

- Die Klasse hat die Klasse `AdminSecured` zu nutzen, um zu bestimmen, dass die entsprechenden, oben erwähnten Methoden ausschließlich von einem `Administrator` gestellt werden können.
- Die Klasse hat die Klasse `Unsecured` zu nutzen, um zu bestimmen, dass die entsprechenden, oben erwähnten Methoden von einem `User` gestellt werden können.
- Die Klasse hat außerdem die Klasse `GraphQLMutationResolver` zu nutzen.
  - Damit erkennt GraphQL, dass es sich hier um ein `Mutation` GraphQL Objekt handelt.
- IMPLEMENTIERUNGSHINWEIS: Des Weiteren ist die Klasse zu dem `SchemaParser` zu hinzufügen.
  - Dies geschieht auf folgender Weise:
    - ```
      SchemaParser.newParser()
      // ...
      .resolvers(new UserMutation())
      ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
