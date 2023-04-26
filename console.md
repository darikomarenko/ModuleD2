Создаём пользователей:
```
user1 = User.objects.create(username=‘Mike’, first_name=‘Frank’
Author.objects.create(authorUser=user1)
User2 = User.objects.create(username=‘Daria’, first_name=‘Komarenko’
Author.objects.create(authorUser=user2)
```

Создаем категории:
```
Category.objects.create(name=‘IT’)
Category.objects.create(name=‘Education’)
Category.objects.create(name=‘Medicine’)
Category.objects.create(name=‘World’)
```

Создаем посты:
```
Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=‘Mike’)),
categoryType=‘NW’, title=‘some title’, text=‘some text’

Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=‘Mike’)),
categoryType=‘AR’, title=‘some article’, text=‘some text here’

Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=‘Daria’)),
categoryType=‘AR’, title=‘some more title’, text=‘some  more text’
```

Присваиваем категории:
```
p1 = Post.objects.get(pk=1)
p2 = Post.objects.get(pk=2)
p3 = Post.objects.get(pk=3)
p4 = Post.objects.get(pk=4)

c1 = Category.objects.get(name='IT')
c2 = Category.objects.get(name='Education')
c3 = Category.objects.get(name=‘Medicine')
c4 = Category.objects.get(name=‘World')
```

Связи:
```
p1.postCategory.add(c1)
p2.postCategory.add(c1, c2)
p3.postCategory.add(c2)
p4.postCategory.add(c3,c4)
```

Комментарии: 
```
Comment.objects.create(commentUser=User.objects.get(username='Mike'), commentPost= Post.objects.get(pk=1), text='comment text 1’)
Comment.objects.create(commentUser=User.objects.get(username='Mike'), commentPost= Post.objects.get(pk=2), text='comment text 2’)
Comment.objects.create(commentUser=User.objects.get(username='Daria'), commentPost= Post.objects.get(pk=3), text='comment text 3’)
Comment.objects.create(commentUser=User.objects.get(username='Daria'), commentPost= Post.objects.get(pk=4), text='comment text 4')
```

Лайк/не лайк:
```
Post.objects.get(pk=2).like()
Post.objects.get(pk=1).like()
Post.objects.get(pk=4).like()
Post.objects.get(pk=1).like()
Post.objects.get(pk=1).dislike()
Post.objects.get(pk=4).dislike()

Comment.objects.get(pk=1).like()
Comment.objects.get(pk=2).like()
Comment.objects.get(pk=3).dislike()
Comment.objects.get(pk=4).like()
```

Обновление рейтинга:
```
Author.objects.get(authorUser=User.objects.get(username='Mike')).update_rating()
Author.objects.get(authorUser=User.objects.get(username=‘Daria')).update_rating()
```

Вывести:
```
Author.objects.get(authorUser=User.objects.get(username='Mike')).ratingAuthor
Author.objects.get(authorUser=User.objects.get(username=‘Daria')).ratingAuthor

best = Author.objects.all().order_by('-ratingAuthor').values('authorUser', ‘ratingAuthor')[0]
```

Вывести дату добавления и username:
```
bestPost = Post.objects.all().order_by(‘-rating’)[:1]
for i in bestPost:
i.dateCreation
i.author.authorUser
i.rating
i.title
i.preview
```

Вывести все комментарии:
```
for k in bestPostCom:
    k.dateCreation
    k.commentUser
    k.rating
    k.text
```




