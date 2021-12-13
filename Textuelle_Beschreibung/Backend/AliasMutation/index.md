# Klassenbeschreibung

## Zweck

Die Klasse dient dazu, sogenannte Mutationen, die ein `Administrator` in Bezug auf den Daten eines `Alias`ses tätigen kann, zu ermöglichen. \
Dabei sind Mutationen Anfragen, die Daten verändern.

## Einschränkungen

Um die Mutation tätigen zu können, muss der Anfrager der Mutation ein `Administrator` sein.

## Methoden

### addAlias(aliasSuggestion : AliasSuggestion, mapID : MapID) : Boolean

- Parameter
  - aliasSuggestion
    - der Alias-Vorschlag, der als Bezeichner für das entsprechende Kartenobjekt fungieren soll
  - mapID
    - die ID des Kartenobjekts, dessen Alias-Vorschlag hinzugefügt werden soll
- Rückgabewert
  - Boolean
    - wahr, wenn der gewünschte Alias erfolgreich hinzugefügt werden konnte, sonst falsch
- Zweck
  - ermöglicht das Hinzufügen eines Alias-Vorschlags zu einem globalen Alias, d.h. modelliert das Annehmen eines Alias-Vorschlags

## Abhängigkeiten

- Die Klasse hat die Klasse `AdminSecured` zu nutzen, um zu bestimmen, dass die Mutationen ausschließlich von einem `Administrator` gestellt werden können. \
- Die Klasse hat außerdem die Klasse `GraphQLMutationResolver` zu nutzen. \
  - Damit erkennt GraphQL, dass es sich hier um ein `Mutation` GraphQL Objekt handelt. \
- IMPLEMENTIERUNGSHINWEIS: Des Weiteren ist die Klasse zu dem `SchemaParser` zu hinzufügen. \
  - Dies geschieht auf folgender Weise:
    - ```
      SchemaParser.newParser()
      // ...
      .resolvers(new UserMutation())
      ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
