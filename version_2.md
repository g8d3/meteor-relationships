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
    
  # Validations executed before save
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
