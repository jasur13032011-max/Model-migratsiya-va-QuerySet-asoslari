# Model-migratsiya-va-QuerySet-asoslari
man buni gjango ormda qildimmmmmmmmmmmmmmmmm
1 modelni yaratish kodni models.py 
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
shell ichida
# Modelni import qilamiz (myapp o'rniga o'z ilovangiz nomini yozing)
from myapp.models import Post

# 1. .objects.create() orqali bir nechta yozuv qo'shamiz
Post.objects.create(title="Birinchi maqola", content="Django juda qulay karkas.")
Post.objects.create(title="Ikkinchi maqola", content="QuerySet metodlarini o'rganyapmiz.")
Post.objects.create(title="Python haqida", content="Python tilida kod yozish oson va tushunarli.")

# 2. .all() — Barcha yozuvlarni olib beradi
all_posts = Post.objects.all()
print(all_posts)
# Natija: <QuerySet [<Post: Birinchi maqola>, <Post: Ikkinchi maqola>, <Post: Python haqida>]>

# 3. .filter() — Shartga mos keluvchi ro'yxatni qaytaradi
filtered_posts = Post.objects.filter(title__icontains="maqola")
print(filtered_posts)
# Natija: <QuerySet [<Post: Birinchi maqola>, <Post: Ikkinchi maqola>]>

# 4. .get() — Aynan bitta yozuvni ob'ekt ko'rinishida oladi
single_post = Post.objects.get(id=1)
print(single_post.title)
# Natija: Birinchi maqola
print(single_post.content)
# Natija: Django juda qulay karkas.
