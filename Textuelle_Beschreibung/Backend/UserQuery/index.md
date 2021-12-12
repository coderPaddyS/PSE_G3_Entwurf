# Beschreibung

Die Klasse dient dazu, Anfragen, die keine Daten verändert und die ein `User` stellen kann, zu ermöglichen. \
Um die Anfragen stellen zu können, muss der Anfrager demzufolge ein `User` sein. \
Mögliche Anfragen sind:
  - Alias-Vorschläge zu einem Kartenobjekt anzeigen lassen
  - Suchen nach einem Kartenobjekt
Die Klasse hat somit die obigen Anfragen zur Verfügung zu stellen. \
Dies geschieht durch folgende Methoden (Reihenfolge hier entspricht der obigen Reihenfolge):
  - ```
    showAliasSuggestions(mapID) : List<aliasSuggestion>
    ```
  - ```
    searchMapObject(searchString) : mapID
    ```
Die Klasse hat die Klasse `Unsecured` zu nutzen, um zu bestimmen, dass die Anfragen ausschließlich von einem Benutzer gestellt werden können. \
Die Klasse hat außerdem die Klasse `GraphQLQueryResolver` zu nutzen. \
Damit erkennt GraphQL, dass es sich hier um ein `Query` GraphQL Objekt handelt. \
Des Weiteren ist die Klasse zu dem `SchemaParser` hinzugefügt werden. \
Dies geschieht auf folgender Weise:
  - ```
    SchemaParser.newParser()
    // ...
    .resolvers(new UserQuery())
    ```
[Quelle zum Nachlesen](https://www.graphql-java-kickstart.com/tools/schema-definition/)
