# meteor-relationships
Define Meteor Collections in a concise way.

```
Post = new MCollection([
  ' name      String'
  ' name      String'
  ' createdAt Date'
], {
  validations: [Function]
  callbacks: [Function]
})
```

```
Post = new MCollection({
  name:      String
  ids:       Array
  createdAt: Date
}, {
  before: 
    create: [
      -> name.length > 5
      -> ids.all(Integer)
      -> createdAt >= Time.now()
    ]
    read:   [Function]
    update: [Function]
    delete: [Function]
  after:
    create: [Function]
    read:   [Function]
    update: [Function]
    delete: [Function]
})
```
