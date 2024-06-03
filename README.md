
# Insertion d'un tableau de bord

## Création d'un environnement virtuel

```sh
python -m venv mon_environnement
```

```sh
mon_environnement/Scripts/activate
```

```sh
pip install django
```

```sh
django-admin startproject TP
```

```sh
cd TP 
```

```sh
python manage.py startapp tp1
```

Créer les dossiers `templates` et `static` au niveau de l'emplacement du projet.

Éditer le fichier `settings.py` qui se trouve au niveau du projet :

```python
'DIRS': [BASE_DIR / 'templates'],

STATIC_URL = 'static/'
MEDIA_URL = 'images/'

STATICFILES_DIRS = [
    BASE_DIR / 'static'
]

STATIC_ROOT = BASE_DIR / 'staticfiles'
MEDIA_ROOT = BASE_DIR / 'images'
```

Créer et éditer le fichier `urls.py` du projet :

```python
from django.contrib import admin
from django.urls import path, include
from django.conf.urls.static import static
from django.conf import settings

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('testo.urls')),
]

urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```

Éditer le fichier `urls.py` de l'application :

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.BASE, name='BASE'),
]
```

Éditer le fichier `views.py` de l'application :

```python
from django.shortcuts import render

def BASE(request):
    return render(request, 'base.html')
```

Créer un fichier `base.html` dans le dossier `templates`.

Déplacer les dossiers `static` de votre tableau de bord vers le dossier `static`.
