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
  authorId:  belongsTo
  tagIds:    Array
  createdAt: Date
}, {
  before: 
    create: [
      -> name.length > 5
      -> ids.all(Number)
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

Rails like:

```
Post = new Model ->
  belongsTo  'author'
  hasMany    'tags'
  field      'name', String
  timestamps
  # createdAt and updatedAt might be used singularly
  
  # All functions return true to continue with process, else null is returned
  before
    create: [Function]
    read:   [Function]
    update: [Function]
    save:   [Function] # This is both create and update
    delete: [Function]
    
  after
    create: [Function]
    read:   [Function]
    update: [Function]
    save:   [Function] # This is both create and update
    delete: [Function]
    
  # $ given ! is not allowed
  present   'name'
  format    'name', RegExp || Function || [RegExp] || [Function]
  format$   'name', RegExp || Function || [RegExp] || [Function]
  present   'tags'
  inclusion 'tags', [Number] || [Tag]
```

And option to add callbacks and validations later

```
Post.after.create [Function] || Function || String
Post.validates.presence String
```


# Mental notes

What I miss from Rails:

1. Not having to define a schema that is already defined on database
2. In the case of Mongo where there is no schema already defined, at least having all those great methods to define relationships, validations and callbacks
3. The nesting ability, send a map of objects and create records in different collections/tables all being validated/callbacked

I don't like to use the validations callbacks though, because callbacks are enough for my preference. Ambiguous.
