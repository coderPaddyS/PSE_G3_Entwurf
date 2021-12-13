# Klassenbeschreibung

## Zweck

Die Klasse dient dazu, sogenannte Mutationen, die ein `Administrator` in Bezug auf den Daten eines `User`s tätigen kann, zu ermöglichen. \
Dabei sind Mutationen Anfragen, die Daten verändern.

## Einschränkungen

Um die Mutation tätigen zu können, muss der Anfrager der Mutation demzufolge ein `Administrator` sein.

## Methoden

### addAdmin(name : String) : Boolean

- Parameter
  - name
    - der Name des Administrators, der hinzugefügt werden soll
- Rückgabewert
  - Boolean
    - wahr, wenn der gewünschte Administrator erfolgreich hinzugefügt werden konnte, sonst falsch
- Zweck
  - ermöglicht das Anlegen eines Administratorzugangs

### removeAdmin(adminID) : Boolean

- Parameter
  - adminID
    - die ID des gewünschten Administrators, der gelöscht werden soll
  - Rückgabewert
    - Boolean
      - wahr, wenn der gewünschte Administrator erfolgreich gelöscht werden konnte, sonst falsch
- Zweck
  - ermöglicht das Entfernen eines Administratorzugangs


## Abhängigkeiten

- Die Klasse hat die Klasse `AdminSecured` zu nutzen, um zu bestimmen, dass die Mutationen ausschließlich von einem `Administrator` gestellt werden können.
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
