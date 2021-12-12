# Beschreibung

Die Klasse dient dazu, sogenannte Mutationen, die ein `User` tätigen kann, zu ermöglichen. \
Dabei sind Mutationen Anfragen, die Daten verändern.
Um die Mutation tätigen zu können, muss der Anfrager der Mutation demzufolge ein `User` sein. \
Mögliche Mutationen sind:
  - Vorschlagen eines globalen Aliasses für ein Kartenobjekt
  - Bewerten (positiv oder negativ) eines Alias-Vorschlags
Die Klasse hat somit die obigen Mutationen zur Verfügung zu stellen. \
Dies geschieht durch folgende Methoden (Reihenfolge hier entspricht der obigen Reihenfolge):
  - ```
    suggestAlias(mapID)
    ```
  - ```
    evaluateAliasSuggestion(aliasSuggestion)
    ```
Die Klasse hat die Klasse `Unsecured` zu nutzen, um zu bestimmen, dass die Mutationen ausschließlich von einem Benutzer gestellt werden können. \
Die Klasse hat außerdem die Klasse `GraphQLMutationResolver` zu nutzen. \
Damit erkennt GraphQL, dass es sich hier um ein `Mutation` GraphQL Objekt handelt. \
Des Weiteren ist die Klasse zu dem `SchemaParser` zu hinzufügen. \
Dies geschieht auf folgender Weise:
  - ```
    SchemaParser.newParser()
    // ...
    .resolvers(new UserMutation())
    ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
