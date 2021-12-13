# Klassenbeschreibung

## Zweck

Die Klasse dient dazu, Anfragen, die keine Daten verändern und die in Bezug zu einem `User` stehen, zu ermöglichen. \

## Einschränkungen

Um die Anfragen stellen zu können, muss der Anfrager demzufolge ein `Administrator` sein. \

## Methoden

### getAliasSuggestions(userID) : List\<aliasSuggestion>

- Parameter
  - userID
    - die ID des Benutzers, dessen Alias-Vorschläge man zurückgegeben haben möchte
- Rückgabewert
  - List\<aliasSuggestion>
    - die Liste mit den Alias-Vorschlägen des gewünschten Benutzers
- Zweck
  - gibt eine Liste der Alias-Vorschläge des gewünschten Benutzers zurück

## Abhängigkeiten

- Die Klasse hat die Klasse `AdminSecured` zu nutzen, um zu bestimmen, dass die Anfragen ausschließlich von einem Administrator gestellt werden können. \
- Die Klasse hat außerdem die Klasse `GraphQLQueryResolver` zu nutzen. \
  - Damit erkennt GraphQL, dass es sich hier um ein `Query` GraphQL Objekt handelt. \
- Des Weiteren ist die Klasse zu dem `SchemaParser` hinzugefügt werden. \
  - Dies geschieht auf folgender Weise:
    - ```
      SchemaParser.newParser()
      // ...
      .resolvers(new UserQuery())
      ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
