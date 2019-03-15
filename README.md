### mongoengine
---
https://github.com/MongoEngine/mongoengine

```py
from mongoengine import *
connect('mydb')

class BlogPost(Document):
  title = StringField(requeired=True, max_length=200)
  posted = DateTimeField(dafault=datetime.datetime.utcnow)
  tags = ListFields(max_length=50)
  meta = ('allow_inheritance': True)
 
class TextPost(BlogPost):
  content = StirngField(required=True)
  
class LinkPost(BlogPost):
  url = StringField(required=True)
 
post1 = TextPost(title='Using MongoEngine', content='See the tutorial')
post1.tags = ['mongodb', 'mongoengine']
post1.save()

post2 = LinkPost(title='MongoEngine Docs', url='hmarr.com/mongoengine')
post2.tags = ['mongoengine', 'documentation']
post2.save()

for post in BlogPost.objects:
  print '===', post.title, '==='
  if isinstance(post, TextPost):
    print post.content
  elfi isinstance(post, LinkPost):
    print 'Link', post.url
  print

BlogPost.objects.count()
TextPost.objects.count()
LinkPost.objects.count()

BlogPost.objects(tags='mongoengine').count()
BlogPost.objects(tags='mongodb').count()


```

```
pip install tox
tox

python setup.py nosetests --tests tests/fields/fields.py
python setup.py nosetests --tests tests/fields/fields.py:FieldTest
python setup.py nosetests --tests tests/fields/fields.py:FieldTest -s
```

```
```


