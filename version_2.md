Rails like:

```
Model 'Post', ->
  belongsTo  'author'
  hasMany    'tags'
  field      'title', String
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
    
  # Validations executed before save,
  # i.e. these are shortcuts to define commonly used callbacks
  # $ given ! is not allowed
  present   'title'
  format    'title', RegExp || Function || [RegExp] || [Function]
  format$   'title', RegExp || Function || [RegExp] || [Function]
  present   'tags'
  inclusion 'tags', [Number] || [Tag]
```

And option to add fields, callbacks and validations after definition:

```
Post.field 'body', String
Post.after.create [Function] || Function || String
Post.present 'title'
```
