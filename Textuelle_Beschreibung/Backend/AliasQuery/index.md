# Klassenbeschreibung

## Zweck

Die Klasse dient dazu, Anfragen über Aliasse, die keine Daten verändern, zu ermöglichen.

## Einschränkungen

Um die Anfragen stellen zu können, muss der Anfrager ein `Administrator` sein.

## Methoden

### getAliasSuggestions(mapID) : List\<aliasSuggestion>

- Parameter
  - mapID
    - die ID des Kartenobjekts, dessen Alias-Vorschläge man zurückgegeben haben möchte
- Rückgabewert
  - List\<aliasSuggestion>
    - die Liste mit den Alias-Vorschlägen des gewünschten Kartenobjekts
- Zweck
  - gibt eine Liste der Alias-Vorschläge des gewünschten Kartenobjekts zurück

## Abhängigkeiten

- Die Klasse hat die Klasse `AdminSecured` zu nutzen, um zu bestimmen, dass die Anfragen ausschließlich von einem Administrator gestellt werden können.
- Die Klasse hat außerdem die Klasse `GraphQLQueryResolver` zu nutzen.
  - Damit erkennt GraphQL, dass es sich hier um ein `Query` GraphQL Objekt handelt.
- IMPLEMENTIERUNGSHINWEIS: Des Weiteren ist die Klasse zu dem `SchemaParser` hinzugefügt werden.
  - Dies geschieht auf folgender Weise:
    - ```
      SchemaParser.newParser()
      // ...
      .resolvers(new UserQuery())
      ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
